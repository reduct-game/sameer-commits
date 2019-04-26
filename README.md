## Site for deploying the Reduct(-redux) game

For new features:
1) New levels - select array-booleans (after Ctrl + F8)
2) Autograder/Oracle (node with a ship) - Most levels on "recursion-basics".
3) Level progression (hamburger button - top right)
4) Make your own level - Press Ctrl + F8 and select 'play' from dropdown menu
NOTE - you can add a node to a previously defined level as well (not necessarily 'play')

### Writing your own level

#### Adding a node:
Press Ctrl + F11 to open the 'Add Node' dialogue box. It will ask for the string representation of the node and the segment where the node is to be placed - 'goal', 'toolbox' or 'board'. Press ENTER when you have completed both the fields. It saves previously defined nodes for future use.

#### Defining the node string:
This is the same as writing the node string in a csv file. Defining new features (marked with a $$) need some special care explained later. Some examples:
<br>
**Definig function**<br>
    `function addOne (x) { return (x) + 1; }`  
    `function myRepeat(num, func, value){ return num == 0 ? _ : func(myRepeat(_, func));}`

**Defining if blocks**<br>
    `_ == _ ? 5 : 4`  
    `num => num == addOne(5) ? true : false`  

**Defining references($$)**
    You can use ***previously*** defined references directly anywhere on board or toolbox.  
    `addOne`  
    `doNothing`  
    etc...  
NOTE - if you are defining references in toolbox with `__unlimited` tag, you need to add the corresponding tag in the csv file when you download it.  

**Defining autograder($$)**<br>
To define an autograder, you can use the following syntax:  
       `__autograder(i)` where i ranges in {0,...,4}  
       `__autograder(0)` is ***adversarial***, i.e it will look for a pair where user defined function breaks. If no such pair exists, it returns the first pair at index 0. 

-If you are defining an autograder(with index i), you should define a missing node `_` in the goal at the ith position so that autograder can fill it later.

-If you are defining an autograder, you need to add input and output fields to csv manually. Using autograder(i) requires at least *i* input-output pairs to be defined in CSV. 

#### When do you need to modify csv manually:
* Adding modifiers such as __unlimited, __argumentAnnotated to the nodes has to be done manually
* You need to define input and output lists manually in csv if you are using an autograder

#### Downloading CSV
When you are done making a level, press Ctrl + F8 and click on **Capture State Graph**. A pop up will be displayed asking you for a *textGoal*. Give a value to the textgoal (or leave it empty) and press ENTER. Your level will be downloaded.


