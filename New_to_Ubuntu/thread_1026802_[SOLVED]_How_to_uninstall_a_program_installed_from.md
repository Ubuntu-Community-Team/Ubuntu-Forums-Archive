---
title: "[SOLVED] How to uninstall a program installed from a binary?"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by GrahamM on 2008-12-31
I downloaded an install program for Skypemate phones named install-Skypemate.

I installed this as follows:

chod +x install-Skypemate
./install-SkypeMate

This brought up a menu asking if I wanted to install which I did.

An icon appeared on the Desktop that linked to the Skypemate file now located in /usr/bin.

I would now like to un-install Skypemate since it does not work properly and I have it on Windows anyway. The program has caused hundreds of messages to appear at startup and shutdown saying Yealink unexpected response - fd. 

I did a search and found a number of files associated with different kernels with names yealink.ko amd yealink.h . There is one Skypemate file in /usr/bin and a link to it on the desktop. Yealink is the company that Skypemate is associated with.

I know how to uninstall using Synaptic, but how do I properly uninstall a program like this that was installed from a binary file? It does not show up in Synaptic.

---

### Post by drs305 on 2008-12-31
Normally when you install an app in the manner you described it creates a folder with either an uninstall script or instructions in a readme file. If you still have the installation folder you can look for an uninstall file or a folder called *postinst* or some other name - there isn't a standard. (That is one of the reasons why using apt/dpkg/synaptic is recommended - standardized methods of keeping track of what is installed and where.)

If you don't have the folder, you can go to the install web site and look for uninstall directions (or install directions that might give you some hints).  You can also do a google search, or you can even do a reinstall and see if you can find an uninstall process the second time around.

---

### Post by donkyhotay on 2008-12-31
> **GrahamM said:**
> I know how to uninstall using Synaptic, but how do I properly uninstall a program like this that was installed from a binary file? It does not show up in Synaptic.

Short answer, with great difficulty. Sometimes the entire program will be stored within one folder at which point you just delete that folder. If that isn't the case I generally just delete the binary file itself. The problem is this often leaves library & data files lying around. Although a hard drive search will probably turn up the data files deleting library files can be a little bit dangerous as deleting the wrong file or a file shared with another program can have undue side effects. As DRS mentioned you can often find instructions either through google or the software makers website.

---

### Post by GrahamM on 2008-12-31
> **drs305 said:**
> Normally when you install an app in the manner you described it creates a folder with either an uninstall script or instructions in a readme file. If you still have the installation folder you can look for an uninstall file or a folder called *postinst* or some other name - there isn't a standard. (That is one of the reasons why using apt/dpkg/synaptic is recommended - standardized methods of keeping track of what is installed and where.)

If you don't have the folder, you can go to the install web site and look for uninstall directions (or install directions that might give you some hints).  You can also do a google search, or you can even do a reinstall and see if you can find an uninstall process the second time around.

Thanks for the reply, but no useful readme, no uninstall, no postinst. Checked vendor websites but could not find uninstall instructions. Tried re-install, but it doesn't have an uninstall. Google doesn't come up with anything.

So, if I just delete everything Yeoman or Skypemate, how can I reove whatever runs during startup and shutdown that causes the error messages? Must be in a scipt somewhere?

---

### Post by GrahamM on 2008-12-31
> **donkyhotay said:**
> Short answer, with great difficulty. Sometimes the entire program will be stored within one folder at which point you just delete that folder. If that isn't the case I generally just delete the binary file itself. The problem is this often leaves library & data files lying around. Although a hard drive search will probably turn up the data files deleting library files can be a little bit dangerous as deleting the wrong file or a file shared with another program can have undue side effects. As DRS mentioned you can often find instructions either through google or the software makers website.


I can delete the entire program and the Yeoman files. But will that stop the error messages - Is there something embedded elsewhere that affects startup and shutdown?

---

### Post by drs305 on 2008-12-31
> **GrahamM said:**
> I can delete the entire program and the Yeoman files. But will that stop the error messages - Is there something embedded elsewhere that affects startup and shutdown?

If the app starts during boot, you can check the /etc/init.d folder to see if the app is included. If you find it in that folder, there will also be links in the /etc/rcX folders which will need to be removed. In addition, you might check the contents of the /etc/rc.local *file*.

---

### Post by GrahamM on 2008-12-31
> **drs305 said:**
> If the app starts during boot, you can check the /etc/init.d folder to see if the app is included. If you find it in that folder, there will also be links in the /etc/rcX folders which will need to be removed. In addition, you might check the contents of the /etc/rc.local *file*.


I delketed everything that mentioned SkypeMate, Skypemate or Yealink (not yeoman !) One main program and a nunch of .ko and .h files . The errors are no longer there during startup and shutdown.


I decided to check the init.d folder. BUT, I can't get it to open! It indicates how many files there are, but then just hangs! I restarted and it still does that! In meantime, I can do other things. I get a message that says:
> 
"init.d - File Browser" is not responding.

You may choose to wait a short while for it to continue or force the application to quit entirely.

It never does display the files.

Seems one problem just leads to another :(

---

### Post by drs305 on 2008-12-31
> **GrahamM said:**
> Seems one problem just leads to another :(

Take heart, it's almost a new year! Or maybe it already is for you.

Another way of checking the /etc/init.d folder is with a search:
```

sudo find /etc/init.d -iname yea*
sudo find /etc/init.d -iname skype*

```

If you aren't getting any more errors it may be time to end this hunt and celebrate the end of 2008! ;-)

Happy New Year!

---

### Post by GrahamM on 2009-01-01
> **drs305 said:**
> Take heart, it's almost a new year! Or maybe it already is for you.

If you aren't getting any more errors it may be time to end this hunt and celebrate the end of 2008! ;-)

Happy New Year!

Happy New Year to you too drs and to all the other helpful people on this forum!

Somehow my access to the init.d folder has recovered, I have no errors when booting or shutting down and Skypemate has been eradicated!

Now let's see what else I can break! (To me it's a good way of finding my way around Ubuntu and seeing what it can and t for me.)

Let's all have a great 2009!

---

