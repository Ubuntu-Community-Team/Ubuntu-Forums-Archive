---
title: "3 things i need to do in order to be better with Linux"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by Messyhair42 on 2010-01-14
I routinely come across three things that i dont know how to do that would make my linux experience easier


the first is using the command ```
sudo mkdir
```
usually i'm trying to make a directory in a folder such as /usr and it tells me i dont have permissions. so question the first, what is the proper way to use the mkdir command?


second is moving files and directories with ```
sudo mv
```
simple question, what is the proper structure of the command, using /home folders


lastly is installing software that i didn't find through USC or SPM but instead downloaded a .deb or a .tar.gz. usually dl to the desktop. what's the proper way to unpack them if i want them under /usr?

Thank you for your help

---

### Post by halitech on 2010-01-14
sudo mkdir should work in any location. I wouldn't suggest using sudo if making folders in your home folder but should work everywhere else.

sudo mv /path/to/file /path/to/new/location

.deb files you should be able to install using sudo dpkg -i <filename.deb>

tar files will normally have a readme file to explain how to install it.

---

### Post by quinnten83 on 2010-01-14
or you can just doubleclick the .deb file.

---

### Post by qchapter on 2010-01-14
Hi Messy,

A good place to start learning about the Linux command line tools are the man pages for the tools you want to use.

For example for mv, open a terminal and type man mv.

For your other two questions:

man mkdir
man dpkg

Most all of linux command line tools have man(manual) pages with instructions on how to use the tool.

Have fun, learning the cli is a very rewarding experience.  :-)

-qchapter

---

### Post by audiomick on 2010-01-14
do you know about 
```
man
```
to open manual pages?

```
man man
```
to find out about the thing itself. Then,

```
man mkdir
```
```
man mv
```

or 
```
man <whatever your wondering about>
```

---

### Post by running_rabbit07 on 2010-01-14
> **halitech said:**
> sudo mkdir should work in any location. I wouldn't suggest using sudo if making folders in your home folder but should work everywhere else.

sudo mv /path/to/file /path/to/new/location

.deb files you should be able to install using sudo dpkg -i <filename.deb>

tar files will normally have a readme file to explain how to install it.

Good info.

---

### Post by J V on 2010-01-14
> **Messyhair42 said:**
> usually i'm trying to make a directory in a folder such as /usr and it tells me i dont have permissions. so question the first, what is the proper way to use the mkdir command?Man is your freind :P

man mkdir says:
```
sudo mkdir <dir name>
```


> what is the proper structure of the command, using /home foldersThis involves learning unix filesystems...

If you are in home:
file is ~/file
. is ~
.. is /home
/file is /file (duh)
file/file is ~/file/file

etc...

```
mv arg1 arg2
```if arg1 is one file, arg2 can be a directory or a file (in which case its like renaming it)
if arg1 is multiple files, arg2 is the directory to move them

> lastly is installing software that i didn't find through USC or SPM but instead downloaded a .deb or a .tar.gz. usually dl to the desktop. what's the proper way to unpack them if i want them under /usr?just double-click debs, thats basicly what dynaptic does when it installs something

tar.gz is usually sourcecode, but you can run it from anywhere... Generally the convention with unpackaged apps is to put them in /opt (idk, thats what I heard)

The first two problems can be made DRAMATICALLY easier with one simple command:
```
gksudo nautilus
```

---

### Post by nishant.singh28 on 2010-01-14
An even easier option. Install Ubuntu tweak. In that you get an option to enable scripts. Enable the one that says Browse as root. Now right click anywhere in Nautilus and goto Scripts-->Browse as root...A new Window opens up with super user permissions. Now do all you want to do.
I know gksudo nautilus sounds easier but if you do this once, it'll be more convenient later on.

---

### Post by audiomick on 2010-01-14
> **nishant.singh28 said:**
> 
I know gksudo nautilus sounds easier but if you do this once, it'll be more convenient later on.

but be careful. If you are working as root, you have the right to break your system...:o

---

### Post by J V on 2010-01-14
Install ubuntu tweak all for gksudo nautilus? I just added it as a shortcut, you only have to do it once and its a hella lot easier than going into scripts :P

---

### Post by nishant.singh28 on 2010-01-14
> **J V said:**
> Install ubuntu tweak all for gksudo nautilus? I just added it as a shortcut, you only have to do it once and its a hella lot easier than going into scripts :P
Uhhh...that was just a choice guys. I use it mainly to change the location of my default audio, video and other folders. What's the problem ?

---

