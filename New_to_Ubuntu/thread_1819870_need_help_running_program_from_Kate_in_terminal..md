---
title: "need help running program from Kate in terminal."
date: 2011-08-06
forum: New to Ubuntu
---

### Post by kd7vea on 2011-08-06
Hello everyone, I am needing some help on running a program.  I will give you a little background.  I have a bachelors degree in computer science, and I am learning perl at the moment (something to add to the Resume).  I am also getting a bit more familiar with Ububntu.  here is what I amtrying to figure out.  I am starting at the begaining like every other language with the "hello world" program.  I type out the program in cate, save it in my home/document directory, and then try to run it in the terminal.  I change the directory to home/document and try to run the helloworld program but it gives me a compilation error, but if I copy and paste the code to the command line, it prints Hello Worldjust as it should.  I just cant find out how to run a program that is written in Kate.  thanks everyone.
Jake

---

### Post by Basher101 on 2011-08-06
Could you post what you wrote in kate here? i am sure that people will find the issue faster

---

### Post by kd7vea on 2011-08-06
sorry, Igot in a hurry and forgot to post the code.

I wrote this in Kate.
perl -e 'print "Hello, World!\n";'

I saved the file as "helloworld", and I saved it in the home/jake/documents directory.when I paste the code directly to the command prompt, it runs fine. when I try to run the file from Kate, this is what I get


jake@jake-HP-530-Notebook-PC:~$ cd /home/jake/Documents/
jake@jake-HP-530-Notebook-PC:~/Documents$ perl helloworld
syntax error at helloworld line 1, near "perl -e "
Execution of helloworld aborted due to compilation errors.
jake@jake-HP-530-Notebook-PC:~/Documents$ 

Thans again
Jake

---

### Post by Miljet on 2011-08-06
Could be one of two problems. First you have to make the file executable by setting the executable bit. See "man chmod" for how to do that. 

When you attempt to run the file, it has to be entered as ./<filename>. The single period stands for current directory. Unlike Windows, Linux does not look for a file in the current directory unless you specify. Otherwise, it only looks in directories that are in your path.

---

### Post by idoitprone on 2011-08-06
> **kd7vea said:**
> sorry, Igot in a hurry and forgot to post the code.

I wrote this in Kate.
perl -e 'print "Hello, World!\n";'

I saved the file as "helloworld", and I saved it in the home/jake/documents directory.when I paste the code directly to the command prompt, it runs fine. when I try to run the file from Kate, this is what I get


jake@jake-HP-530-Notebook-PC:~$ cd /home/jake/Documents/
jake@jake-HP-530-Notebook-PC:~/Documents$ perl helloworld
syntax error at helloworld line 1, near "perl -e "
Execution of helloworld aborted due to compilation errors.
jake@jake-HP-530-Notebook-PC:~/Documents$ 


Thans again
Jake

isnt having the command perl -e in the file then use perl to run the file kidda redundent?
I believe what you want is to have the header of 
```
#!/bin/bash
```
on top of the file
and use
```
./helloworld
```
to run the command
dont forget to add execute permissions
```
chmod u+x helloworld
```

---

### Post by babakott on 2011-08-06
I am no Perl expert, but wouldn't you just type
```
print "Hello World\n";
```
into the helloworld file, then call it from Perl like this: $perl helloworld

edit: Looks like you have a better answer already.

---

### Post by jacksaff on 2011-08-06
You're telling perl to run with the text file as input. The first part of that file is 'perl' which perl doesn't know what to do with. 
Edit your file to print "Hello, World!\n"; and run it with perl helloworld and you should get the behaviour you want.

Alternately, with your original file you change it's permissions to executable and just run it with ./helloworld

Haha! beaten to it!

---

### Post by idoitprone on 2011-08-06
> **babakott said:**
> I am no Perl expert, but wouldn't you just type
```
print "Hello World\n";
```into the helloworld file, then call it from Perl like this: $perl helloworld

edit: Looks like you have a better answer already.

the op has a choice
The op does not have to use
```
$perl helloworld
```all he has to do is 
```
./helloworld
```but he has to put the right header, if he does
```
 #!/usr/bin/perl 
 print "Hello World.\n";
```
[http://perl.about.com/od/gettingstartedwithperl/a/testperl.htm](http://perl.about.com/od/gettingstartedwithperl/a/testperl.htm)

I not a perl expert either and i am not planning on learning perl.

---

### Post by kd7vea on 2011-08-07
Thanks guys, it working now. As I said, I am just trying to add Perl to my resume, but I am also learning a bit about Linux at the same time. I have always programmed in a Windows environment, but I am finding myself using ubuntu more and more. I am sure I will have more questions, but its good to know there are some good groups out here to help out. Thanks again.
Jake

---

