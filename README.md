<p align="center"><img src="https://github.com/sc-1123/ufdse/blob/master/logo.jpg", width="355px", height="461px"></p>
<h1 align="center">Un Fin De Semana Especial</h1>  
<p align="center">Magnificent demos in python.</p>  
  
- [▶ before we start...](#1)  
- [▶ walk through the indices](#2)  
- [▶ ancient sorting algorithm](#3)  
- [▶ Daily Prophet](#4)
- [▶ code and the key of secrets](#5)
- [▶ Iterating through the non-iterable!](#6)
- [▶ while in for](#7)
- [▶ mathmatican's special](#8)
- [▶ very last end](#9)
  
<h2 id="1">before we start...</h2>  
WARNING:  
  
Don't!  
  
Ever!  
  
Dream!  
  
About!  
  
Using!  
  
These!  
  
Code!  
  
In!  
  
Work!  
  
<h2 id="2">walk through the indices</h2>  
We sometimes use these code to iterate through indices:  
  
```  
for x in range(len(iterable)):  
    dosomething 
```  

Well, why not use some wrappings?  
  
```  
indices = lambda iterable: range(len(iterable)) 
  
for x in indices(iterable): 
    dosomething 
```  
  
<h2 id="3">ancient sorting algorithm</h2>  
Abacus is a really old thing for us.  
Well, sometimes ancient gives us new ideas.  
  
```  
def abacus_sort(array: list):
    col_sight = [0] * max(array)
    row_sight = [0] * len(array)
    for i in array:
        for col in range(i):
            col_sight[col] += 1
    
    for col in col_sight:
        for row in range(col):
            row_sight[row] += 1
    
    row_sight.reverse()
    return row_sight
```  
  
This algorithm simulates an abacus. The integers are number of beads on each row.  
It sets the abacus as the array we put inside, then  
flip it and make it stand on the ground. Now you see, the abacus has been sorted automatically!  
  
<h2 id="4">Daily Prophet</h2>  
If you want to see what a list looks like when append a thing, or insert a thing, or pop a thing?  
  
```  
class Prophet:
    @staticmethod
    def see_append(array, item):
        return array + item
    
    @staticmethod
    def see_insert(array, idx, item):
        return array[:idx] + [item] + array[idx + 1:]
    
    @staticmethod
    def see_pop(array, idx):
        return array[:idx] + array[idx + 1:]
```  

You can use it as you imported a module named `Prophet`.  
  
<h2 id="5">code and the key of secrets</h2>  
If you want to have a map that uses list or set as key, is it possible?  
  
Yes!  
  
```
class AnykeyMap:
    def __init__(self, mappings):
        self.keys = ()
        self.values = ()
        for key, value in mappings:
            self.keys += (key,)
            self.values += (value,)
    
    def __getitem__(self, key):
        return self.values(self.keys.index(key))
    
    def __setitem__(self, key, value):
        idx = self.keys.index(key)
        self.values = self.values[:idx] + (value,) + self.values[idx + 1:]
    
    def __delitem__(self, key):
        idx = self.keys.index(key)
        self.keys = self.keys[:idx] + self.keys[idx + 1:]
        self.values = self.values[:idx] + self.values[idx + 1:]
```  
  
You can find something similar with the `Prophet` class. Unfortunately, for reducing the memory, we need to deal with tuples,  
not lists.  

<h2 id="6">Iterating through the non-iterable!</h2>  
When you want to iterate through an integer by indices like lists and strings, how?  
  
```  
class IterableInt:
    def __init__(self, integer):
        self.integer = integer
        self.string = str(integer)
        self.curr = 0
    
    def __next__(self):
        if self.curr >= len(self.string):
            raise StopIteration
        return_val = int(self.string[self.curr])
        self.curr += 1
        return return_val

    def __iter__(self):
        return self
```  
  
<h2 id="7">while in for</h2>
Is it possible to implement a while loop by for loop?  
  
Yes!  
  
```  
class While_loop:
    def __init__(self, expr):
        self.expr = expr
    
    def __next__(self):
        if not eval(self.expr):
            raise StopIteration
        return

    def __iter__(self):
        return self
```  
  
And a demo for the demo:  
  
```  
from random import randint
    i = 1
    for _ in While_loop('i != 0'):
        i = randint(0, 10)
        print(i)
```  
  
You'll see these if run it for several times (may not identical, this is the result I got):  
  
```  
first:
7
0
second:
1
9
0
third:
3
9
3
2
1
4
0
```  
  
real magic!  
  
<h2 id="8">mathmatican's special</h2>  
How to get a line's expression by two dots on it?  
  
```  
def line_expr(p1, p2):
    x1, y1 = p1
    x2, y2 = p2
    m = (y2 - y1) / (x2 - x1)
    b = y2 - m * x2
    return lambda x: m * x + b
```  
  
But I thought it will be long...  
  
<h2 id="9">very last end</h2>
Well, if you're a nut and you do want to use those code, you don't need to copy.  
  
Use pip or original install command to make it!
