---
title: "where is perl?  Why no directory listings"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by caye on 2009-08-31
I have many problems tonight with Ubuntu 9.04.. 
first in the terminal mode when i do an ls -gla or just ls I do not get a listing of the directors and files, instead i get just a number.. it seems like every damn minute ubuntu is changing on my desktop and it is getting well beyond reasonable. 

2. problem is I have been trying to run Perl. after getting it to run the other night. i am again
experiencing the same problem.  
if i type perl -v i get the version so I know it is installed. awa I also reinstalled it
5.10.1  something. tonight my perl print command quite  working. 
which perl produced /usr/bin/perl
but the same line that worked last night now does not work (this on again off again happens a lot  one time the same lines work the next time it does not..) how can that be?
#!/usr/bin/per print "hello /n";  will not work.. tonight but did last night 
please tell me how to discover the cause of this variable behavior? 		                   		  		  		  		  		 		 			 				

I tried locate perl and got so many could not determine.. who do I find the directory to direct by #! to for perl..???

How do I get the directors to show when I do an ls -gla.. 

this is beyond reasonable

---

### Post by ibutho on 2009-08-31
To find out where perl is installed do
```
which perl
```
On my system, the output is /usr/bin/perl.

I'm not sure how to help with ls. Did you change something on your system or edit any config files?

---

### Post by lkraemer on 2009-08-31
In a Terminal window do:
```

man ls

```
then use spacebar to page forward, b to page up, and q to exit.

Your command should be one of these samples:
```

ls -gla
ls -alt
ls -F

```
as shown by the man ls command.


Table B.1. Overview of DOS/Linux commands
DOS commands	Linux command
<command> /? 	man <command> or command --help
cd 	cd
chdir 	pwd
cls 	clear
copy 	cp
date 	date
del 	rm
dir 	ls
echo 	echo
edit 	vim (or other editor)
exit 	exit
fc 	diff
find 	grep
format 	mke2fs or mformat
mem 	free
mkdir 	mkdir
more 	more or even less
move 	mv
ren 	mv
time 	date

You need a sample perl script to execute.  Google for "example perl
script".
EXAMPLE:
```

#!/usr/bin/perl
print "Hello, Perl!\n\n";

```
Save the code as test.pl, then change permissions to make it executable,
run from a terminal with:
```

perl test.pl

```

lkraemer

---

### Post by slakkie on 2009-08-31
use 
```

#!/usr/bin/env perl

```

You can replace perl for any app if you want, bash, zsh, python, etc etc.

---

### Post by DaithiF on 2009-08-31
Hi, this may not be related to your ls problem, but why would you run ls -**gl**a ?
from the manpage:
```
        -g     like -l, but do not list owner
        -l     use a long listing format

```
so you either use -l or you use -g, but both together doesn't seem to make sense.

this may not be the cause of your problem of course.  
can you post the output you get when you run ls, and also the output from
```
alias ls
which ls

```

---

### Post by caye on 2009-09-01
I got by that monster.. perl is #!/usr/bin/perl  print 'beginner /n/';  printed but only when the print command and content were on the same line as the shabang

Is there a free editor that people use in perl?
thanks for all the help.

---

### Post by holycow131415 on 2009-09-01
bluefish, its the editor for everything =)

---

### Post by caye on 2009-09-02
app get install bluefish 
is the command to get and install bluefish on ubuntu

seems so I installed using this on command line, 
but had to do sudo app get install bluefish. 

now though my perl print command is not working. 
which perl produced /usr/bin/perl
but the same line that worked last night now does not work (this has been the case for the past week one time it works the next time it does not..) how can that be?
#!/usr/bin/per print "hello /n";  will not work.. tonight but did last night 
please tell me how to fix this variable behavior?

---

