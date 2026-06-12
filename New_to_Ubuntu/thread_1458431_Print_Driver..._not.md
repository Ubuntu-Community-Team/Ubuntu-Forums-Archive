---
title: "Print Driver... not"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by noworldorder on 2010-04-20
Ubuntu doesn't have the driver for my Samsung ML-1915.

I downloaded the Linux driver but it doesn't work as Ubuntu wants a "postscript printer description" file. Where would I find this? And ideas?

Thanks - Chris

FYI I really appreciate all the help I have been given ever since I got hooked on Ubuntu a few weeks ago.

---

### Post by ibizatunes on 2010-04-20
[http://www.samsung.com/ca/consumer/detail/support.do?group=office&type=printer-multifunction&subtype=monochrome-laser&model_nm=ML-1915&disp_nm=ML-1915&language=&cate_type=all&dType=D&mType=DR&vType=&prd_ia_cd=06010400&model_cd=ML-1915/XAA&menu=download](http://www.samsung.com/ca/consumer/detail/support.do?group=office&type=printer-multifunction&subtype=monochrome-laser&model_nm=ML-1915&disp_nm=ML-1915&language=&cate_type=all&dType=D&mType=DR&vType=&prd_ia_cd=06010400&model_cd=ML-1915/XAA&menu=download)

untar the file, and run the installer

---

### Post by noworldorder on 2010-04-20
thanks but the installer wont run.  IT gives the option of running or running in terminal more.  Neither option works.  

I tried connecting it as a generic text only printer.  When I tried to print a test page it said:  error during CUPS operation. client-error-document-format-not-supported.

---

### Post by LewRockwell on 2010-04-20
[http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)

.

---

### Post by noworldorder on 2010-04-20
Thanks Lew - but do you really think I can do this?  Looks scary but I will give it a shot.  

'Government is a disease masquerading as its own cure"

---

### Post by noworldorder on 2010-04-21
stuck at the first step:

1. Add the following line to your /etc/apt/sources.list, by editing the file as root (or using sudo), or by using Synaptic or other GUI to add a repository.  	Code:
 	deb [http://www-personal.umich.edu/~tjwatt/suldr/](http://www-personal.umich.edu/~tjwatt/suldr/) debian extra 
I installed vim to edit the text (was that a good idea?) but I don't know how to do it.

I don't seem to be able to paste the code in the editor - something strange happens and half of it is where I pasted it and the other half is at the bottom of the terminal.

Newbie needs help!

---

### Post by noworldorder on 2010-04-23
I am trying to follow the instructions on this page:

[http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)

I completed the first couple steps (I had to learn how to edit etc/apt/sources.list) but I am stuck with this command:  apt-key add suldr.gpg

This is what happens:

root@chris-laptop:~# apt-key add suldr.gpg
gpg: can't open `suldr.gpg': No such file or directory


Any thoughts?
thanks ~ chris

---

