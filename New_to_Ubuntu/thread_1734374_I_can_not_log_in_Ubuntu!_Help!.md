---
title: "I can not log in Ubuntu! Help!"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by Ymurti on 2011-04-20
When I turn on my laptop after some time comes this message:

Install Problem!

The Configuration defaults for Gnome Power Manager have not been installed correctly. Please contact your computer administrator.


Please help me!

Yajna

---

### Post by terwase on 2011-04-20
The most probable cause for this would be that you have a broken package.
There are two ways round this, the first is
      1.Go to synaptic package manager and locate the power manager program and remove/or reinstall it.
      2.run sudo apt-get and repair broken packages, you should search the forums because there is an exhaustive tutorial (in my opinion more concise than the official documentation) on this subject and more others.

---

### Post by Lovek on 2011-04-20
I have the same problem and found this thread .   [http://ubuntuforums.org/showthread.php?p=10698429#post10698429](http://ubuntuforums.org/showthread.php?p=10698429#post10698429)  

it has as possible solution the the partion on which you have ubuntu, is full - and provides instructions on how to solve this
waiting for further instructions there..


good luck to us!

---

### Post by leviathan8 on 2011-04-20
Can you access a tty? Try CTRL + ALT + F1. Login using your username and password, then type in "sudo service gdm stop". After doing this, boot again your X session with "startx" (be careful not be use sudo on this one). If you're dropped into GUI, it's ok. You can proceed by reinstalling gnome-power-manager. However, if this doesn't work, you can just use the virtual console to remove it. Being given that you're in a tty, type the following:

```
sudo apt-get purge gnome-power-manager
```

Then remove the configuration file from your home directory:

```
rm ~/.gconf/apps/gnome-power-manager
```

And finally reinstall it:

> sudo apt-get install -y gnome-power-manager

Note that you can use both the GUI and virtual console to input these commands into a terminal.

---

### Post by Ymurti on 2011-04-20
Thank you leviathan8,

Bear in mind, I am a begginer.

>Can you access a tty?< 
 
What is it???? 

>Try CTRL + ALT + F1 < 

I did and came a terminal and this ubuntu@ubuntu:~$ 

>Login using your username and password<

How I do that?

---

### Post by Ymurti on 2011-04-21
Thank You all, I solved the problem. When the error message came I pressed Ctrl+Alt+F2 then I logged in and used the rm command to delete some files from my home folder. Then restarted and everything was normal again. 

Ubuntu is great.

Hare Krishna

---

### Post by Lovek on 2011-04-21
> **Ymurti said:**
> Thank You all, I solved the problem. When the error message came I pressed Ctrl+Alt+F2 then I logged in and used the rm command to delete some files from my home folder. Then restarted and everything was normal again. 

Ubuntu is great.

Hare Krishna
that sounds great! 
how do I know what the files are named?  i.e. what should I actually write after the rm command?

all the best, L

---

