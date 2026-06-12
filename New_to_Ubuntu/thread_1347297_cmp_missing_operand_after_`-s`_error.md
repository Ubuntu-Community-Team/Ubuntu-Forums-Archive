---
title: "cmp: missing operand after `-s` error"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by varsha upadhyaya on 2009-12-06
hi myself varsha, can anyone help me out 

#!/bin/bash 

cmp -s $1 $2 

if [ $? -gt 0 ]; 
then 
cat $1>>animals 
cat $2>>animals 
echo contents are not equal and copied into another file 
else 
echo contents are equal 
fi 

if i run this it gives error as
cmp: missing operand after `-s`
cmp: try `cmp --help` for more information.
this wont come to the prompt . i will press ctrl+z to come to prompt.

---

### Post by anewguy on 2009-12-06
I copied/pasted your script and saved as test.sh.  I then changed permissions on test.sh to make it executable.  I then ran the following test:

dave@dave-desktop:~$ ./test.sh 1 2
cat: 1: No such file or directory
cat: 2: No such file or directory
contents are not equal and copied into another file
dave@dave-desktop:~$ 

A 'ls' showed the "animals" file had been created but was empty as it should be given the script.

Don't know what you might be doing wrong - did you try copying/pasting the script in your post back as your actual script file, setting permission to execute, then running as per above?

Dave :)

---

### Post by varsha upadhyaya on 2009-12-07
thank u dave. i got the result. but it is not showing the else part. if u can find out whats my mistake then please do reply. thanks again. 

:-) varsha

---

