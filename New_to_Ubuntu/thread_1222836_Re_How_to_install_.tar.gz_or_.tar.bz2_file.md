---
title: "Re: How to install .tar.gz or .tar.bz2 file?"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by faiyez on 2009-07-25
Hey guys I'm a super noob.

I looked into the install file inside my tar.bz2 and it has step by step instructions, but I still don't get it. Here's step 1:

> 1. [b]`cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.[/b]  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

What is the cd command and how do I use it to locate my tar? Let's suppose I put it in /home/user

---

### Post by aysiu on 2009-07-25
Tell us what you're trying to install, and we'll help you get it installed.

This is a good place to start, though:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by SunnyRabbiera on 2009-07-25
Yeh we dont install software here like on windows, so no more going to website a.b, x to get what you want for a majority of the software you need.
What are you trying to install?

---

### Post by deadspider187 on 2009-07-25
> **faiyez said:**
> Hey guys I'm a super noob.

I looked into the install file inside my tar.bz2 and it has step by step instructions, but I still don't get it. Here's step 1:

What is the cd command and how do I use it to locate my tar? Let's suppose I put it in /home/user

Open the application menu and go to Accessories-->Terminal.  This is where all commands are entered.

In the terminal, run the command given earlier in this thread to extract the files from the archive.  Then, if the files are in /home/user/extractedfoldername, you would type "cd /home/user/extractedfoldername".

You will need to run "sudo aptitude install checkinstall" to install applications in a way Ubuntu can manage removal of them in the future.

Run these two steps to compile and install an application in Ubuntu:

./configure <enter>
make checkinstall make install <enter>

This assumes a lot of things, like the application doesn't need any specific installation instructions, you have all of the dependencies (applications and libraries this program expects you to have), and a whole range of other variables.

What application are you trying to install?  There may be a much easier way for you to install it.

---

