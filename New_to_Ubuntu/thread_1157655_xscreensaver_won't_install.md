---
title: "xscreensaver won't install"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by Dragunov308 on 2009-05-12
Help, I'm a n00b.  I want to install xscreensaver-5.08.  I downloaded it to my fresh install of Ubuntu 8.10.  I right clicked it and "Extract Here" the xscreensaver-5.08.tar.tar file.  I run "sudo apt-get install xscreensaver".  It tells me that "Package xscreensaver is not available".  However the follwoing packages replace it "xscreensaver-data".  So I run "sudo apt-get install xscreensaver-data".  It tells me that it's already the newest version.   I try running "xscreensaver-demo".  It tells me "The program xscreensaver-demo is currently not installed.  You can install it by typing: sudo apt-get install xscreensaver".  I am in an endless loop.  I've tried Google and this is my last resort before I pitch my computer out the window.

---

### Post by Walter Melon on 2009-05-12
What did you get when you extracted the .tar file?  did it have a readme or an installation file?

---

### Post by Dragunov308 on 2009-05-13
Yes, it had a readme file.  It didn't really help though, it said that same thing as what I posted above.

---

### Post by Dragunov308 on 2009-05-13
I think that I will go back to Windows.  I just tried the same thing on a different computer with Ubuntu on it, and the same thing is happening.  I don't understand what I'm doing wrong.  Am I not suppose to extract the .tar.tar file?

---

### Post by Walter Melon on 2009-05-13
were you in the right directory when you tried the apt-get install command?

---

### Post by spillin_dylan on 2009-05-13
Have you tried installing from Synaptic?  That's what I did, and it worked perfectly.

---

### Post by Dragunov308 on 2009-05-18
No, I have not tried Synaptic.  I don't even know what that is.  I will google it to find out.  I will try anything.  Thanks.

---

### Post by Ms_Angel_D on 2009-05-18
> **Dragunov308 said:**
> Help, I'm a n00b.  I want to install xscreensaver-5.08.  I downloaded it to my fresh install of Ubuntu 8.10.  I right clicked it and "Extract Here" the xscreensaver-5.08.tar.tar file.  I run "sudo apt-get install xscreensaver".  It tells me that "Package xscreensaver is not available".  However the follwoing packages replace it "xscreensaver-data".  So I run "sudo apt-get install xscreensaver-data".  It tells me that it's already the newest version.   I try running "xscreensaver-demo".  It tells me "The program xscreensaver-demo is currently not installed.  You can install it by typing: sudo apt-get install xscreensaver".  I am in an endless loop.  I've tried Google and this is my last resort before I pitch my computer out the window.

Sudo apt-get is the command used to install packages from the synaptic package manager. If you had to download the file, apt-get will not install that file.

The synaptic package manager is located under the menu "System -> Administration"

also you might want to visit "System -> Administration -> Software sources" and make sure you have the extra repositories checked under the "third Party Software" tab.

---

