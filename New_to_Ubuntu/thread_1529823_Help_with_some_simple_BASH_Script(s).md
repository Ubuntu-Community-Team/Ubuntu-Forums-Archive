---
title: "Help with some simple BASH Script(s)"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by klemperal on 2010-07-12
I'm having a lot of trouble trying to create a couple bash scripts.  The first bash script I'm trying to create is a sort of "change directory" script where it first lists the current directory of the user, then lists the directory to which the user wants to go, and then goes there.  So far, all I could come up with what you see below.
```
#!/bin/bash

echo "moving from"
pwd
echo "to"
?????????
pwd
```

The other script I'm trying to create is just a sort of "go back to previous directory."

If you have any idea on how I can go about making either of the aforementioned scripts, please let me know.

---

### Post by Nano Geek on 2010-07-13
I don't know if this is the best way to do it, but you could have the to and from directories as variables. For example:```
$goingto = /home/user
$movingfrom = /home/user/Desktop

echo "Moving from " $movingfrom " to " $goingto
cd $goingto
```I haven't done Bash scripting in a while, so I can't be sure this code is correct, but something like that might work for you.

---

### Post by yaaarrrgg on 2010-07-13
This code will hop back to a previous directory:

```
cd - 

```

By default, this will hop to your home dir:

```
cd 

```

---

### Post by Paqman on 2010-07-13
> **klemperal said:**
> The first bash script I'm trying to create is a sort of "change directory" script where it first lists the current directory of the user, then lists the directory to which the user wants to go, and then goes there.

How does the script know the destination directory? You can use something like:
```
echo "Enter the path to the destination: "
read destination
```

Then you can use $destination as a variable. Can you tell us exactly what you're trying to achieve with this? It'd be easier for us to help if we knew why you were writing a script to do this.

---

