---
title: "python programming"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by scorpious on 2011-04-24
Sorry about the long post. I hope it makes sense.

I'm attempting to create a table in python that looks like this

3 . . .
2 . . .
1 . . .
. a b c

where the rows and columns can be anywhere up to a 9x9 table depending on the raw_input


Anyway I can get a table to look like with this

 . . . .
 . . . .
 . . . .
 . . . .

 whick is great but when I try to put the number in I'm stuck

I'm using the function

def assign_letters(grid):
    print grid
    list = grid
    count = 0
    number = len(list) - 2
    start = 3
    while count <= number:
        list [count][0] = start
        print list
        count += 1
        start = start - 1
    return list

where 'grid' is a list with four other lists in it [['.', '.', '.', '.'], ['.', '.', '.', '.'], ['.', '.', '.', '.'], ['.', '.', '.', '.']]

Now that function work fine by itself and I get the result[[3, '.', '.', '.'], [2, '.', '.', '.'], [1, '.', '.', '.'], ['.', '.', '.', '.']] if I put the lists in directly. But as soon as I import a list I get the result...
[[1, '.', '.', '.'], [1, '.', '.', '.'], [1, '.', '.', '.'], [1, '.', '.', '.']]

I'm very confused

here's the entire programme if someone's interested.

Player_number_score = 0
player_letter_score = 0
#nums = ['1','2','3','4','5','6','7','8']
#letters = ['a','b','c','d','e','g','h','i']

def start():
    size = (raw_input("Board size: "))
    number = ['2','3','4','5','6','7','8','9']
    while size not in number:
        print 'must be between 2 and 9'
        size = (raw_input("Board size: "))
    size = int(size)
    return size


def set_up(n):
    row = []
    grid = []
    count = 0
    while count != n:
        row.append('.')
        count += 1
    count = 0
    while count != n:
        grid.append(row)
        count += 1
    return grid
    
def assign_letters(grid):
    print grid
    list = grid
    count = 0
    number = len(list) - 2
    start = 3
    while count <= number:
        list [count][0] = start
        print list
        count += 1
        start = start - 1
    return list
    
    
    
    
grid_size = start()
grid = set_up(grid_size)
grid = assign_letters(grid)
print grid

---

### Post by orange2k on 2011-04-24
I think you should ask this in the programing section of the forum...;)

---

### Post by rosencrantz on 2011-04-24
I'd use numpy arrays:
```
from numpy import *
grid=array([['.']*4]*4)
grid[:-1,0]=(arange(3)+1).astype(str)[::-1]
#If you need a nested list, you can convert back:
grid=grid.tolist()

```
And use code tags, so we can check your indentations.

---

