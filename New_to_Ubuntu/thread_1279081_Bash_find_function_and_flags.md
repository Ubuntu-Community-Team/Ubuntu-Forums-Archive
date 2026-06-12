---
title: "Bash: find function and flags"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by rutledmj on 2009-09-30
Im working on a program that searches a designated folder for files with many names then prints them out.  This is what i have so far:

```
#!/bin/bash

dir=.
dir=$1

find $dir ! -type d -links +1 -exec ls -i {} \; | sort | awk '{ if(inode==$1) { print "  "$2 } else { inode=$1; print inode ";"; print "  "$2 }}'
```Im trying to get it so that if you put an -m flag before you specify the directory that if a file has one or more names that were not found in the searched subtrees, a line is output after the list of filenames specifying how many names are missing.

I have no idea how to do this.

---

### Post by boblemur on 2009-10-01
sorry but i find your question rather unclear, are you trying to find a specific file? or are you trying to find any files that match a list of files? if so, how do you want the input, what are some examples of input and output for the program you are trying to make.

what does it currently do, and what would you like it to do differently.

please be specific with your io and exactly what you are searching for please so we can better help you.

---

### Post by rutledmj on 2009-10-01
sorry if it is unclear.  let me try to explain better.

currently the find function will list all files in the current directory that has more than one name (ie more than one link).  When the program executes with the command "bash lnkls" it outputs a files inode followed by a list of all of the files names.

for example:
inode1:
[INDENT]file1
file2
[/INDENT]inode2:
[INDENT]filea
fileb
[/INDENT]
I would like the program to also let me know how many files are outside of the current directory with the same name but only when the -m flag is being used.

for example:

$ bash lnkls -m

inode1:
[INDENT]file1
file2
[/INDENT]Missing: 1
inode2:
[INDENT]filea
fileb
[/INDENT]Missing: 4

i hope this is clearer

---

### Post by A_Fiachra on 2009-10-01
This is really NOT absolute beginner talk -- now is it?


:-)

If ou are looking for files outside the current directory you will need to save filename and fine on each.


Or you could not do this is bash and use a more structured programming language with a nested for loop??

But, why do you want to find directories outside the current directory with the same name?

Is this a homework assignment?

---

### Post by boblemur on 2009-10-01
so as said above, your probably better off doing this in a programming language such as python.

however if you need to for some reason do this in bash then(i hope im understanding correctly):

you would need to find files throughout all of / then grep -v any that have $dir as the start of the directory (this may need absolute referencing to be used however) then run it through wc -l (word count program with the line count flag).

also have a look at locate (much faster), although not as exhaustive as find (in my experience).

for example to find all pdf files:
```
locate *.pdf
```
have a look at the manpage to see if it supports the parts of find that you wanted.
```
man locate
```


good luck :) correct me if this isnt what you are trying to do.

ps: A_Fiachra, sure the post might be in the wrong category, but does that mean that he needs any less help? it is rather starter bash, absolute beginner is for beginners to the server distribution also so if there bash questions are welcome, then why shouldn't rutledmj's be welcome? this community is great because of the help it can provide so if he is able to be helped posting in beginners, then its appropriate.

---

### Post by slakkie on 2009-10-01
Have a look at getopts

```

while getopts man opt ; do
  case $opt in
    m) do_stuff $OPTARG;;
    a) do_other_things $OPTARG;;
    n) something_else;;
  esac
done

```

If you then create functions you can do do_stuff when -m is called, or do_other_things if -a is used as an argument of your script.

For your find question I don't have an answer.

---

### Post by unutbu on 2009-10-01
rutledmj, the find command can print the inode, the filename, and the number of hard links:
```

find . ! -type d -links +1 -printf '%i %f %n\n' 
```

For example, if 

dir1 contains file1 and file2 (which shares the same inode) and 
dir2 contains file3 which shares the same inode, then the command above (run inside dir1) will print something like
```

7905740 file2 3 
7905740 file1 3 
```

Thus you get two lines with the same inode, but each line reports 3 hard links exist.
Using awk or some other programming language you should be able to figure out how many files are missing without having to search the entire hard drive. (I can whip up a python solution if you are interested.)

PS. You may have to be careful with how you process the lines if your filenames contain spaces.

---

