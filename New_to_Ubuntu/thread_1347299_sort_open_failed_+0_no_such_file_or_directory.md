---
title: "sort: open failed: +0: no such file or directory"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by varsha upadhyaya on 2009-12-06
hi this is again me varsha. 

while true 
do 
   clear 
   cat emp.lst 
   echo enter the field to be sorted 
   echo "1.name 2.eid 3.salary" 
read ch 
case $ch in 
 1)sort -t ":" +0 emp.lst;; 
 2)sort -nt ":" +1 emp.lst;; 
 3)sort -nt ":" +2 emp.lst;; 
 *)exit;; 
esac 
read sl 
done 
set -x 

if i run this it asks for the option and if i press 1 or 2 or 3 it gives an error 
sort: open failed: +0: no such file or directory

---

### Post by lloyd_b on 2009-12-06
I'm assuming that the data file is in the form "name:eid:salary".  What exactly are you expecting "+0" "+1" and "+2" to do?  You should be using the "-k #" option of sort to tell it which field to sort by:```
case $ch in
    1)sort -t ":" -k 1 emp.lst;;
    2)sort -nt ":" -k 2 emp.lst;;
    3)sort -nt ":" -k 3 emp.lst;;
    *)exit;;
esac
```will do what I *think* you want.

Lloyd B.

---

### Post by varsha upadhyaya on 2009-12-07
hi, thanks . i got the result. but it is sorting only on the basis of name. what to do to sort from emp id or emp salary. can u tell me how to enter these data into the file?

---

### Post by lloyd_b on 2009-12-07
> **varsha upadhyaya said:**
> hi, thanks . i got the result. but it is sorting only on the basis of name. what to do to sort from emp id or emp salary. can u tell me how to enter these data into the file?

I don't understand the problem.  Here's the data file I used for testing:```
fred:3:500
barney:6:300
slate:1:2000
dinocrane:2:800
``` and the exact shell script (it's a slightly modified version of your original post) ```
#!/bin/bash

while true
do
    clear
    cat emp.lst
    echo enter the field to be sorted
    echo "1.name 2.eid 3.salary"
    read ch
    case $ch in
        1)sort -t ":" -k 1 emp.lst;;
        2)sort -nt ":" -k 2 emp.lst;;
        3)sort -nt ":" -k 3 emp.lst;;
        *)exit;;
    esac
    read sl
done
set -x
``` and when running it, I get the following:```
fred:3:500
barney:6:300
slate:1:2000
dinocrane:2:800
enter the field to be sorted
1.name 2.eid 3.salary
1
barney:6:300
dinocrane:2:800
fred:3:500
slate:1:2000

fred:3:500
barney:6:300
slate:1:2000
dinocrane:2:800
enter the field to be sorted
1.name 2.eid 3.salary
2
slate:1:2000
dinocrane:2:800
fred:3:500
barney:6:300

fred:3:500
barney:6:300
slate:1:2000
dinocrane:2:800
enter the field to be sorted
1.name 2.eid 3.salary
3
barney:6:300
fred:3:500
dinocrane:2:800
slate:1:2000
```
The question is - what does *your* data file look like?  Since you didn't post a sample of it, I had to make assumptions based on what the shell script was apparently trying to do.

Lloyd B.

---

### Post by varsha upadhyaya on 2009-12-07
hi, thanks a lot . ur assumptions were correct. my file is exactly same. but when i run it is not sorting salary wise properly. i gave the salaries as 8000,20000,40000,80000. but its giving the o/p as the same. but first it should be 80000, then 40000, then 20000, at last it should be 8000. for that what i should do? accept this the program is working fine. thanks once again.

---

### Post by lloyd_b on 2009-12-08
> **varsha upadhyaya said:**
> hi, thanks a lot . ur assumptions were correct. my file is exactly same. but when i run it is not sorting salary wise properly. i gave the salaries as 8000,20000,40000,80000. but its giving the o/p as the same. but first it should be 80000, then 40000, then 20000, at last it should be 8000. for that what i should do? accept this the program is working fine. thanks once again.

Do you mean you want the salary sorted in *descending* order, rather than *ascending* (from highest to lowest, rather than from lowest to highest)?

If so, you need the "-r" option on the sort command to reverse the sort order:```
 3)sort -nrt ":" -k 3 emp.lst;;
```

Lloyd B.

---

### Post by varsha upadhyaya on 2009-12-12
thanks. i got it. where i can get these commands. i mean which book should i refer?

---

### Post by lloyd_b on 2009-12-12
> **varsha upadhyaya said:**
> thanks. i got it. where i can get these commands. i mean which book should i refer?

"man sort" in a terminal window will give you the full syntax reference for the 'sort' command.

Lloyd B.

---

