---
title: "Create my own iso"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by freewind on 2010-11-01
Hello All!
I need in default Ubuntu ISO replace some programms(delete default program and put to install some programms that I'm prefer)and generate my own Ubuntu bootable ISO. How Can I do this? 

Thank you.

---

### Post by TeoBigusGeekus on 2010-11-01
[http://www.ubuntugeek.com/create-custom-ubuntu-live-cd-with-remastersys-in-karmic.html]("http://www.ubuntugeek.com/create-custom-ubuntu-live-cd-with-remastersys-in-karmic.html")

---

### Post by jimstar79 on 2010-11-01
i'm in the process of 'trying' to do the same thing. 

I am right now making a back-up iso with Remastersys - fingers crossed!

I just have one question about this: once the back-up is ready, can I just load up this in  the same way as the Ubuntu LIveCD, and run it without installing the back-up?

Been trying to find the answer to this question for a while. Dont want to insert the back-up CD to find out!

To answer the thread, I found this quite straight forward: 

[http://www.webupd8.org/2010/08/create-full-system-backup-or-custom.html](http://www.webupd8.org/2010/08/create-full-system-backup-or-custom.html)

And the Remastersys website:

[http://www.geekconnection.org/remastersys/info.html](http://www.geekconnection.org/remastersys/info.html)

Following download it took just two or three clicks to get going.

---

### Post by jimstar79 on 2010-11-01
Colorlessprism has created a nice little thread here:

[http://ubuntuforums.org/showthread.php?t=1514043](http://ubuntuforums.org/showthread.php?t=1514043)

---

### Post by ayenack on 2010-11-01
Posted to the wrong thread. Sorry.

---

### Post by ezsit on 2010-11-01
+1 for Remastersys

I've been using the DIST mode for backing up the system minus the /home folder so my backups boot into a default Ubuntu desktop and I can run them live from the DVD or install them with the normal Ubiquity installer. I install all the apps I want, clean the apt cache, run bleachbit to remove unnecessary localizations and temp files, then make my DIST mode backup and test it. I've been using remastersys since the 7.10 release of Ubuntu and it has never let me down. The current version 2.0.17-1 seems to work fine with Ubuntu 10.10, but it has not been officially released for the latest ubuntu yet.

---

