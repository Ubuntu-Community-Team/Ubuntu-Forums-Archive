---
title: "python script help D:"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by makuab on 2010-05-04
```
# Area calculation program

print "Welcome to the Area calculation program"
print "---------------------------------------"
print

# Print out the menu:
print "Please select a shape:"
print "1  Rectangle"
print "2  Circle"
print "3  Square"

# Get the user's choice:
shape = input("> ")

# Calculate the area:
if shape == 1:
    height = input("Please enter the height: ")
    width = input("Please enter the width: ")
    area = height*width
    print "The area is", area

elif shape == 2:
    radius = input("Please enter the radius: ")
    area = 3.14*(radius**2)
    print "The area is", area

elif shape == 3:
    length = input("Please enter the length of one side")
    area = length**2
    print "the area is", area

else:
    # If all else fails...
```I get this error
  
File "yes.py", line 36
    
        ^
IndentationError: expected an indented block

---

### Post by nitstorm on 2010-05-04
ubuntuforums.orgubuntuforums.org/newreply.php
specify something in the last "else" block
```

# Area calculation program

print "Welcome to the Area calculation program"
print "---------------------------------------"
print

# Print out the menu:
print "Please select a shape:"
print "1  Rectangle"
print "2  Circle"
print "3  Square"

# Get the user's choice:
shape = input("> ")

# Calculate the area:
if shape == 1:
    height = input("Please enter the height: ")
    width = input("Please enter the width: ")
    area = height*width
    print "The area is", area

elif shape == 2:
    radius = input("Please enter the radius: ")
    area = 3.14*(radius**2)
    print "The area is", area

elif shape == 3:
    length = input("Please enter the length of one side")
    area = length**2
    print "the area is", area

else:
    # If all else fails...
    print "error"



```

That should do the trick i guess..

---

### Post by makuab on 2010-05-04
> **nitstorm said:**
> ubuntuforums.orgubuntuforums.org/newreply.php
specify something in the last "else" block
```

# Area calculation program

print "Welcome to the Area calculation program"
print "---------------------------------------"
print

# Print out the menu:
print "Please select a shape:"
print "1  Rectangle"
print "2  Circle"
print "3  Square"

# Get the user's choice:
shape = input("> ")

# Calculate the area:
if shape == 1:
    height = input("Please enter the height: ")
    width = input("Please enter the width: ")
    area = height*width
    print "The area is", area

elif shape == 2:
    radius = input("Please enter the radius: ")
    area = 3.14*(radius**2)
    print "The area is", area

elif shape == 3:
    length = input("Please enter the length of one side")
    area = length**2
    print "the area is", area

else:
    # If all else fails...
    print "error"



```That should do the trick i guess..

awesome thanks!

---

### Post by WinterWeaver on 2010-05-04
this should also work.
Remember a comment does not really count as code, so the python interpreter just sees a empty block and thus complains.

```

....
else:
    pass

```

---

### Post by makuab on 2010-05-04
> **WinterWeaver said:**
> this should also work.
Remember a comment does not really count as code, so the python interpreter just sees a empty block and thus complains.

```

....
else:
    pass

```

thanks to you too

---

### Post by Elfy on 2010-05-04
please do not post duplicate threads - you have another on the same thing.

Closed.

[http://ubuntuforums.org/showthread.php?t=1472716](http://ubuntuforums.org/showthread.php?t=1472716)

---

