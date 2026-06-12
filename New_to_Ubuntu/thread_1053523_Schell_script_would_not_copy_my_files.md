---
title: "Schell script would not copy my files"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by nvmedhekar on 2009-01-28
Bash refuses to copy my files, I am dumbfounded!

#!/bin/bash

echo 'Executing for i=1'
# executing a script that run a large computation and creates an output file myout, the script exe runs fine from the prompt
exe
echo "Execution complete"
cp myout myout.1
cat myout >> myout.all

# rerun the script
echo 'Executing for i=2'
exe
echo "Execution complete"
cp myout myout.2
cat myout >> myout.all
----------

This script never creates myout.1 nor it redirects myout.1 into myout.all. However, it does create myout.2 correctly and puts its content in myout.all.

I am very perplexed, please help!

---

### Post by yabbadabbadont on 2009-01-28
Given that there is no way to know from you post what your "exe" does, my best guess would be that the first time that you run it, no "myout" file is created, but the file does get created the second time.  You most likely need to add some debugging statements to your script to figure out what is happening.  I assume that you are running this from inside of a terminal window and are in the proper directory that should contain the "myout" file.

Here is a suggestion as to some debugging statements you might add to your script:
```
#!/bin/bash
echo "Checking for myout* files"
ls -l myout*
echo "Hit enter to continue"
read junk

echo 'Executing for i=1'
exe
echo "Execution complete"

echo "Checking for myout* files"
ls -l myout*
echo "Hit enter to continue"
read junk

echo "Copying myout to myout.1"
cp myout myout.1

echo "Checking for myout* files"
ls -l myout*
echo "Hit enter to continue"
read junk

cat myout >> myout.all

echo "Checking for myout* files"
ls -l myout*
echo "Hit enter to continue"
read junk

# rerun the script
echo 'Executing for i=2'
exe
echo "Execution complete"
cp myout myout.2
cat myout >> myout.all

```

---

