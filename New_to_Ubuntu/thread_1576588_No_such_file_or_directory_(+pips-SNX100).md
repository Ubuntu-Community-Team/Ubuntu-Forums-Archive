---
title: "No such file or directory (+pips-SNX100)"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by rakelspektakel on 2010-09-17
Hi, I am an absolute beginner, I am proud that I have found the  terminal window!!

I have Lucid, and it is not 64 - but the other. (told ya beginner...)

I have managed to find and install some programs/drivers to make my printer work, but realized through a thread here, that I since cannot install any thing. 

In this thread there is a solution,  [http://newyork.ubuntuforums.org/showthread.php?p=7880957](http://newyork.ubuntuforums.org/showthread.php?p=7880957)  but when I try 'accessing' any folder i ALWAYS get "no such file or directory".

f.eks when I write this: 
/var/lib/dpkg/info$ ll | grep pips 
or this
/var/lib/dpkg/info$ sudo mv pips-snx100* /home/rakel/Desktop/pips

This has happened before when trying  to access any file, f.eks. someone described that one should 'cd' once way into a folder, and wrote the code, and I could only get 'no such file or directory'. 

So, firstly, I'm thinking I am typing something wrong...? is there some semicolon or backslash or sth that Ishould know about?

and secondly, what is this pips-snx100 problem all about,  how can a printer file hinder all of my installations?

greatful for any help

---

### Post by themusicalduck on 2010-09-17
When you look at those lines of code you can see often the $ sign in the middle of a line. That sign indicates where the command is entered. Anything before that $ indicates the directory you are currently in and then your username and hostname.

When you first open a terminal you'll see that there is :~$ at the end of the line.

The ~ sign indicates your home space, so the terminal opens in your home space by default.

First make a folder on your desktop to move the files to if you haven't already.```
mkdir ~/Desktop/pips
```

To run those commands you then need to navigate to the right directory. To do this you need to run this in the terminal.```
cd /var/lib/dpkg/info
```

cd is "change directory" and /var/lib/dpkg/info is the directory you want to navigate to (/ stands for "root" a bit like C: on a Windows install).

In the same terminal window, then run every command that is listed after the $. So in this case it is```
ll | grep pips
sudo mv pips-snx100* /home/rakel/Desktop/pips
sudo apt-get -f install
```

Be very careful when using commands like mv or rm, particularly with the sudo command before it. If you mistype something then you could accidentally remove some important files. It's usually best to copy and paste them in. "mv" is move and "rm" is remove. "sudo" gives you access to all files on your system that you wouldn't normally have access to as a normal user. When using it you need to enter your password, no stars will appear, just type you pass in and hit enter.

Hope this is helpful and makes using the terminal a bit clearer! There's a good guide for new users to Ubuntu that has a section on basic use of the terminal here - [www.ubuntu-manual.org](www.ubuntu-manual.org) if you want any further reading on it.

---

### Post by rakelspektakel on 2010-09-21
thank u so much!!!! I was looking for a manual, before I posted, but simply couldn't find answers since I didn't know what I was looking for.

I get it. thank u!! :-)

---

