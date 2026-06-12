---
title: "updating software"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by tadcan on 2009-02-02
I have storybook installed. It is for writing fiction and I am currently using it.  [http://storybook.intertec.ch/joomla/](http://storybook.intertec.ch/joomla/)

There is now an updated version which I have d/l. 

It comes as a .tar.gz file. In windows installing a new file overwrites the old one and keeps the saved data. Does that happen in linux. 

Here is the page for back ups

[http://storybook.intertec.ch/joomla/index.php/faqs/31-general/61-i-want-to-backup-my-files-where-are-they-located](http://storybook.intertec.ch/joomla/index.php/faqs/31-general/61-i-want-to-backup-my-files-where-are-they-located)

I don't see a folder called .storybook in my home folder, but i see other files for the program. 

How can I be sure it wont delete my work if I update?

---

### Post by yeats on 2009-02-02
I'm pretty sure any software worth its salt will check for previously installed versions, so I would think you're okay, but - forgive me for asking - is there a particular feature/set of features that you need from the newer version?  Sometimes the "if it ain't broke, don't fix it" rule is prudent - in my experience, anyway :-).

---

### Post by tadcan on 2009-02-02
It has some new buttons, updated dictionary and some other stuff. I've just begun to use it so the new features may be useful to me or not.

---

### Post by snova on 2009-02-02
> **tadcan said:**
> It comes as a .tar.gz file. In windows installing a new file overwrites the old one and keeps the saved data. Does that happen in linux.

Ordinarily, yes. However .tar.gz files are usually source code, and installing this way can be difficult... though in this case, it looks like it could also be a binary.

> I don't see a folder called .storybook in my home folder, but i see other files for the program.

Press Ctrl-H to view hidden files.

> How can I be sure it wont delete my work if I update?

Because installing a new version of a program doesn't touch your files.

This package you've downloaded might either be source code or a binary- extract it to your desktop (or wherever you like) and show us the contents.

A quick way to tell would be the presence of files named Makefile.in, configure, etc. That's almost certainly source code.

On the other hand, if there's a file named 'storybook' or similar and it's a program, it's a binary build. In this case there really isn't much to do in the matter of installation, just click the program and it should run.

---

### Post by tadcan on 2009-02-03
Thanks ctrl-H worked to find the folder.

From your description I think its a binary. Maybe the screen shoot will be clear enough. 

I just have to remember how I installed it the last time.

---

### Post by zvacet on 2009-02-03
What **install.txt** say about installing?

---

### Post by tadcan on 2009-02-03
The install text gives a link to the website

[http://storybook.intertec.ch/joomla/index.php/installation](http://storybook.intertec.ch/joomla/index.php/installation)

> Extract the file:
$ tar xvf 
 
Install it:
$ ./install.sh

Run it:
$ ./storybook.sh


> tadcan@Quad:~$ tar xvf storybook_2.1.11_linux.tar.gz
tar: storybook_2.1.11_linux.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

It is common for me to be told no such file or directory. Its what normally confuses me when I try to install a .tar.gz file

EDIT: Ok so I double-clicked on install.sh choose run in terminal. There was a flash of something and I now have the updated version. Guess I'm to used to seeing the windows dialogue boxes during the install.

If someone wants to give me a linux 101 explanation about what just happened please do. Guess linux isn't so hard, but it is still confusing.

---

### Post by oldos2er on 2009-02-03
You need to "cd" to the directory where the archive is. If you downloaded it to your desktop, run
```
cd Desktop
```
in a terminal, then 
```
tar zxvf filename.tar.gz
```
then ```
cd filename/
``` 
to enter that directory, then 
```
./install.sh
```
 Naturally you'll need to replace 'filename' with whatever the archive name is.

---

### Post by tadcan on 2009-02-03
Thanks. So I get no file or directory found because I didn't tell the terminal what directory to look in.

It will be hard to know if i understand your steps because I fluked the upgrade.

However in the interest in learning I'll ask some more questions. 

So I got to
> tadcan@Quad:~$ cd Desktop
tadcan@Quad:~/Desktop$ tar zxvf storybook_2.1.11_linux.tar.gz

Then it unzipped the files onto my desktop. So I didn't know which file to put before ./install.sh

Am I understanding this correctly?

---

### Post by oldos2er on 2009-02-04
You might want to install nautilus-open-terminal, which is a script that can open a terminal in any directory you happen to be browsing in the GUI file manager (Nautilus).

 If the folder is on your desktop, note its name, and in a terminal type
```
cd Desktop/stor
```
then hit Tab, which should complete the folder name for you.

---

### Post by tadcan on 2009-02-05
I have downloaded firefox 3.0.6

I run > cd Desktop then > tar xvf firefox-3.0.6.tar.bz2

That gives me a folder on my desktop called firefox. What do i do next to install it?

Edit making some progress

> tadcan@Quad:~/Desktop$ cd firefox
tadcan@Quad:~/Desktop/firefox$ ./configure
bash: ./configure: No such file or directory
tadcan@Quad:~/Desktop/firefox$ firefox/configure
bash: firefox/configure: Not a directory
tadcan@Quad:~/Desktop/firefox$ 


---

### Post by carml on 2009-02-05
Try to manually go (= with the mouse) to that folder,look for the correct path up to the /.configure file you're looking for.Then code the correct path into the terminal.I hope this help you. :)

---

### Post by tadcan on 2009-02-05
Not sure which file to use.

In your example you wrote /.configure 
On a tutorial I saw ./configure 

Which is correct. What is the function of the "." is it part of the command or a place holder for a file name?

I found a file simply called firefox. It was a white page with blue gears. I double clicked on that, chose run in terminal. The box came up and then left. If this worked how do I checked the version of firefox I am running.

---

### Post by oldos2er on 2009-02-05
> **tadcan said:**
> I have downloaded firefox 3.0.6

I run  then 

That gives me a folder on my desktop called firefox. What do i do next to install it?

Edit making some progress

 I believe Firefox comes as precompiled binaries, no compiling necessary.

---

### Post by snova on 2009-02-05
> **tadcan said:**
> What is the function of the "." is it part of the command or a place holder for a file name?

It refers to the current directory. Otherwise Bash would search for the program named "configure" in its standard locations, and not find it.

---

### Post by tadcan on 2009-02-05
from this

> tadcan@Quad:~$ cd Desktop
tadcan@Quad:~/Desktop$ cd firefox
tadcan@Quad:~/Desktop/firefox$ ./firefox
tadcan@Quad:~/Desktop/firefox$ 

firefox launches a new window. I then went to help and about firefox, the version number is still 3.0.5

---

### Post by intertec on 2010-11-06
It's easier now to install Storybook. Have a look here:
[http://storybook.intertec.ch/joomla/index.php/component/content/article/35-installation/127-installation-on-ubuntu](http://storybook.intertec.ch/joomla/index.php/component/content/article/35-installation/127-installation-on-ubuntu)

---

