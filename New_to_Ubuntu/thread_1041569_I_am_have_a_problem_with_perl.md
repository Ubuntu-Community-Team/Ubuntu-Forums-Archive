---
title: "I am have a problem with perl"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by ajlinzey on 2009-01-16
I'm new to perl and I'm having a problem. I started with the 'Hello World' script from the llama book.

#!/usr/bin/perl
print "Hello World!\n";

I made it executable.

$ ls -l HelloWorld
-rwxr-xr-x 1 ajl ajl 40 2009-01-14 19:31 HelloWorld

but if try to run it. I get.
$ HelloWorld
bash: HelloWorld: command not found

man perl works and there is an executable file named perl in /usr/bin.
the man etry for perl says that perlintro should give me an introduction to perl. I get bash: perlintro: command not found.

I tried reinstalling from the synaptic package manager. no help
-Andy

---

### Post by baruch60610 on 2009-01-16
Hi.  The problem is that this program isn't in your 'path', so bash doesn't recognize it.  Even when you're in the same directory as the desired program, it won't run unless you say:

./helloworld

or whatever the name is.  The dot and slash tell bash where the program is that you want to run.  If you're not in the directory, you could type:

/home/user/path/to/program/helloworld

That should help.  You might consider creating a 'bin' directory in your home directory (it would be /home/user/bin, where 'user' is your user name).  Then add this path to your PATH variable.  You can do that by editing the file at /etc/environment (you'll have to do this as root).  Or you can add a line to your .bashrc file in your home directory.

.bashrc is a hidden file, meaning it doesn't show when you do a regular ls listing.  Using ls -a will show those hidden files.  You can edit this file without having to be root.

BTW, there is a Website dedicated entirely to Perl, called Perlmonks.com.  Check it out - it's helpful and interesting.

---

### Post by ajlinzey on 2009-01-16
Thanks. my bad 
-Andy

---

### Post by tr333 on 2009-01-18
> **ajlinzey said:**
> I'm new to perl and I'm having a problem. I started with the 'Hello World' script from the llama book.

#!/usr/bin/perl
print "Hello World!\n";

I made it executable.

$ ls -l HelloWorld
-rwxr-xr-x 1 ajl ajl 40 2009-01-14 19:31 HelloWorld

but if try to run it. I get.
$ HelloWorld
bash: HelloWorld: command not found

man perl works and there is an executable file named perl in /usr/bin.
the man etry for perl says that perlintro should give me an introduction to perl. I get bash: perlintro: command not found.

I tried reinstalling from the synaptic package manager. no help
-Andy

perlintro is not a command itself, but is part of the perl documentation.  This is accessed via the 'perldoc' program.  Run 'perldoc perlintro' to access the perlintro or view it on the web at [http://perldoc.perl.org/perlintro.html](http://perldoc.perl.org/perlintro.html)

---

