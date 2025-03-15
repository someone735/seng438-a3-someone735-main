**SENG 438 - Software Testing, Reliability, and Quality**

**Lab. Report #3 – Code Coverage, Adequacy Criteria and Test Case Correlation**

| Group \#:  28        |
| ----------------- |
| Student Names:      |
| John            |   
| Mark            |   
| Ron             |   
| Lana            |   

(Note that some labs require individual reports while others require one report
for each group. Please see each lab document for details.)

# 1 Introduction

The primary goal of this lab is to explore white box testing using the JUnit framework, along with using EclEmma (coverage tool) that measures how thoroughly our test suite exercises the code. This lab will tell us what we have missed and what have we done for coverage in lab 2 as we dive deeper to learn about the internal structure of the software. This lab will ensure us that all logical statements, branches, and conditions are adequately tested. 

# 2 Manual data-flow coverage calculations for X and Y methods

calculateTotalColumn
![image](https://github.com/user-attachments/assets/d67a8e4a-943e-471c-a4fd-38f7b22370c1)
![image](https://github.com/user-attachments/assets/8c2c1133-ab87-426c-9c97-cd87be7e7247)
![image](https://github.com/user-attachments/assets/a21f603f-cecd-496a-b06c-868a1c66c0ca)

![image](https://github.com/user-attachments/assets/c8eaeb66-c986-4d78-9215-98236b32b43f)

# 3 A detailed description of the testing strategy for the new unit test

Our testing strategy was analysing the old unit tests and the coverage they covered and creating new unit tests that would help the previous tests to full coverage. If the methods were not tested in the assignment 2 and thus do not have any pre-existing unit tests, then in using the coverage tools and the given code, create unit tests that aim for the full coverage of the targeted method. 

# 4 A high level description of five selected test cases you have designed using coverage information, and how they have increased code coverage

Range - expandToInclude

In assignment 2 there were several tests that cover multiple methods such as constrain and combine,etc. Without including the expandToInclude, by writing targeted tests for the expandToInclude method, we ensure that every part of its logic is executed and verified. This means we check what happens when the input range is null, when the value is already within the range, when it’s lower than the current lower bound, or higher than the current upper bound, as well as handling special cases like NaN.

DataUtilities - calculateRowTotal 

Since this method was mainly tested using Mockery which does not work with our current coverage tool, I recreated the tests without using Mockery. After the analysis of these tests using the coverage tool, I found that there were some areas that the old test cases could not reach. The reason for this is because in the calculateRowTotal, there existed a for loop functioning on a condition which would always be false, thus never executing the code inside the for loop. As a result, the instruction coverage for this method would never be 100%.

DataUtilities - getCumulativePercentages

In lab 2, this method was tested using mocking which does not work for coverage. I changed the tests to work for lab 3 which uses no mocking. I replaced the mocks with DefaultKeyedValues, allowing the method to execute properly and improving coverage. Full branch coverage is not possible due to a bugged loop, overall they increased all code coverages. 

DataUtilities - calculateColumnTotal

Mocking was used in the previous assignment which mocked test values which made black box testing simpler. This approach however did not contribute to code coverage at all considering that all of the test cases were using mocking. We used real implementations instead of mocks for this lab about white box testing and the coverage metrics were improved. 


DataUtilities - calculateRowTotal - overload method 

When using the coverage tool, it was found that calculateRowTotal had an overloaded method which took in an additional parameter called validColumns. Using this information, we were able to create additional test cases that used the new parameter, thus increasing our overall code coverage.


# 5 A detailed report of the coverage achieved of each class and method (a screen shot from the code cover results in green and red color would suffice)

![image](https://github.com/user-attachments/assets/55e06694-9487-4668-9437-3617513ac563)
![image](https://github.com/user-attachments/assets/6f1d5ca1-bf22-482c-adf0-b6e459efc36f)
![image](https://github.com/user-attachments/assets/4117736e-2f99-443e-8958-89127746e1d0)

The reason as to why the coverage in getLength, calculateRowTotal, calculateColumnTotal, getUpperBound, getCumulativePercentage are not 100% is because when trying to understand why our tests could not get full 100%, we discovered that there were sections of code that could never be run thus not being able to achieve 100% coverage. This will result in the statement and branch coverage significantly affecting the entirety of the total coverage. Given that multiple methods are affected by this error/bug, the total coverage for all tests will not represent the actual coverage. 

# 6 Pros and Cons of coverage tools used and Metrics you report

A pro to working with EclEmma is its real-time feedback. Specifically the feature to highlight code that was executed and code that could have been executed. This feature helped identify what code still needed to be tested or sections of code that were unreachable. A con to this coverage tool would be its limitations to plug-ins. Specifically being unable to handle mocking plug-in. Since mocking is used for testing complex functions and methods, the inability to provide accurate coverage can lead to sections of code being misrepresented in the coverage.

The metrics we used for this assignment were instruction coverage, branch coverage and method coverage. Method coverage replaced condition coverage as condition coverage was not a metric in our coverage tool

# 7 A comparison on the advantages and disadvantages of requirements-based test generation and coverage-based test generation.

Requirements-based test generation 
- Advantages
  - Ensures the code outputs aligns with the expected requirements 
  - Can help with detecting early signs of defects
- Disadvantages 
  - Dependent on the quality of the requirements assuming it can cover edge/boundary cases 
  - Can cause blind spots in code testing if quality of the requirements is not upheld

Coverage-based test generation
- Advantages
  - Identifies untested areas of code 
  - Can uncover issues undetected in requirement-based test generation
  - Provides a higher consistency in test depth
- Disadvantages 
  - Coverage does not always equate to functionality
  - Can create tests that do not align with requirements 

# 8 A discussion on how the team work/effort was divided and managed

We as a group decided to first work on the methods that we did in lab 2 that did not fully get 100% coverage. So the person that worked on the method in lab 2 works on it for lab 3 as well if it is not already full coverage. For newer methods we created, we decided to just split it evenly where everyone gets 3 and 1 person gets 4. 

Ron - 3 additional methods: scale, shift, clone

Lana - 3 additional methods: hashCode, isNaNRange, expandToInclude

John - 4 additional methods: combineIgnoreNaN, range equals, expand, dataUtilities equal 

Mark - 3 additional methods: getLength, getLowerBound, getUpperBound

# 9 Any difficulties encountered, challenges overcome, and lessons learned from performing the lab

One of the main difficulties we had as a group is that some of the methods cannot reach 100% coverage due to infeasible paths (sections of code that could not be run). This highlighted the challenge of testing flawed implementations and the importance of analyzing coverage reports to identify dead code. Another challenge that our group faced was specifically within the DataUtilities where we had to change our code from lab 2 that used mocking to using real implementations instead. Without using real implementations, we could not get any coverage because mocks do not execute the actual method logic. Rewriting the tests using real implementations helped contribute to overcoming the issues and improving coverage. 

# 10 Comments/feedback on the lab itself

Overall this lab helped us dive deeper into the internal structure of what we did in lab 2 using white box testing instead of black box. We learnt how to use EclEmma which is a tool that tells us the code coverage. The transition from mock-based to real object testing clarified how using these coverage tools work and why direct execution is necessary for accurate metrics. We just had problems with certain parts of methods that contained unreachable code so we cannot get them to 100% coverage. This lab was insightful and reinforced the role of structured testing in software. 
