---
title: "Compile Script Error"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by dcasimir on 2010-07-26
I'm trying to download and use the software accompanying the book "The Art of Molecular Dynamics Simulation." by Dennis Rapaport.

The readme file says to first run the compile script that is attached.

However I'm getting the following cryptic compile errors that I can't seem to solve.

administrator@ubuntu:~/Casimir/artmdsim2$ ./compile.sh
./compile.sh: line 10: syntax error near unexpected token `('
./compile.sh: line 10: `foreach f  (src/pr_*) '

---

### Post by AlphaLexman on 2010-07-26
The script is looking for a shell '/bin/tcsh' that is not installed by default in ubuntu.
To install it... in a terminal type:
```
sudo apt-get install tcsh
```
and enter your password when prompted.

---

### Post by dcasimir on 2010-07-26
Thanks,
However, I did that, but I'm still getting the same error, regarding line 10.

---

### Post by AlphaLexman on 2010-07-26
Let me admit that I know NOTHING about the '/bib/tcsh/' shell!
But, best I can figure, is you are missing a quotation mark of some kind.
I don't know where it should go, I can only guess.

Option 1.
```
# script for testing that programs compile correctly (see README)

#! /bin/tcsh

set CFLAGS = "-I./src"

#set LFLAGS = "-L/usr/local/mpi/lib -lmpich -lpthread -lm"
set LFLAGS = "-lm"

foreach f  ("src/pr_*") 

  echo $f
  gcc $CFLAGS $f $LFLAGS
  rm a.out

end
```Option 2.
```
# script for testing that programs compile correctly (see README)

#! /bin/tcsh

set CFLAGS = "-I./src"

#set LFLAGS = "-L/usr/local/mpi/lib -lmpich -lpthread -lm"
set LFLAGS = "-lm"

foreach f  ('src/pr_*') 

  echo $f
  gcc $CFLAGS $f $LFLAGS
  rm a.out

end
```Copy the above options, save them as compile1.sh compile 2.sh
Don't forget to make them executable:
```
chmod +x compile1.sh compile2.sh
```

---

### Post by dcasimir on 2010-07-26
After following your suggestions of putting quotations somewhere, I did resolve the error about line 10, and now it looks maybe like I need to do something ( I don't know what) before running this script. The edited script with the quotes you suggested is attached.

Here's what I got below.

gcc: no input files
rm: cannot remove `a.out': No such file or directory
Casimir/artmdsim2/compile.sh: line 16: end: command not found

---

### Post by AlphaLexman on 2010-07-26
Well, the first line of the script says it is a test script, and the script is trying to remove a file that doesn't exist. I wouldn't worry about that.
Move on with the README file.

---

### Post by AlphaLexman on 2010-07-26
Can you post / attach the README file?

---

### Post by dcasimir on 2010-07-27
Here it is.

---

### Post by dcasimir on 2010-07-27
Sorry, Here's the readme, ubuntu forums wouldn't let me attach it without a .txt extension.

---

### Post by dcasimir on 2010-07-27
third try.

---

### Post by AlphaLexman on 2010-07-27
What directory are you in when your run the script?

[LIST]
[*]~/
[*]~/artmdsim2
[*]~/artmdsim2/src
[*]~/artmdsim2/data
[*]somewhere else
[/LIST]
I am still guessing, but I don't think the quotes should be on the outside of the parenthesis.
```
foreach f  '(src/pr_*)'
```The manpage for tcsh:
> **foreach** *name* **(***wordlist***)**One other thing, put the:
```
#!/bin/tcsh
```on the first line of the script. Notice I removed the 'space' between the '!' and '/'

Good Luck :-?

---

### Post by dcasimir on 2010-07-27
I usually run the script from /artmdsim2

I'll remove the quotes and try the last correction concerning the first line also.

---

### Post by dcasimir on 2010-07-28
Removed the quotes from around the parentheses.
No luck, got the same error about line 10.

Thanks for all the suggestions,

---

### Post by AlphaLexman on 2010-07-28
From README:
> Please notify the author of errors or any other problems. Suggestions for
enhancing the collection, as well as reports on how this material is used, will
be greatly appreciated. The author's e-mail address is:
[EMAIL="rapaport@mail.biu.ac.il"]rapaport@mail.biu.ac.il[/EMAIL].

---

### Post by dcasimir on 2010-07-30
Below is what the author said. It worked.

[COLOR=Navy]Thanks for your query.
 
To get started, if you don't have tcsh, I suggest doing the following:
 
Compile -
gcc -o pr_02_1 src/pr_02_1.c -lm
 
Copy the required data file -
cp data/pr_02_1.in .
 
Run job -
./pr_02_1
 
Hope that works.
 
----------------------------------------------------
Dennis C. Rapaport
Department of Physics, Bar-Ilan University
Ramat-Gan, Israel 52900
tel: (972) (3) 531-8048      fax: (972) (3) 738-4054
email: [email]rapaport@mail.biu.ac.il[/email]
web: [http://www.ph.biu.ac.il/~rapaport]("http://www.ph.biu.ac.il/%7Erapaport")[/COLOR]

---

