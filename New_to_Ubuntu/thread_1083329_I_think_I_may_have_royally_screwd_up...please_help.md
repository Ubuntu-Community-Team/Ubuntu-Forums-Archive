---
title: "I think I may have royally screwd up...please help!"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by gerz85 on 2009-02-28
I have a Dell Mini 9 that had Ubuntu 8.04.1 preinstalled.  I upgraded to 8.10 without a hitch.  I also installed UNR but decided that I wanted to remain in desktop mode.  Compiz wasn't working so I decided to do a fresh install and start over.

I followed the same exact steps that i had used from 8.04 to 8.10 using a LiveUSB.  I went through the whole process, but I ran into problems when creating partitions.  Either way, I completed the installation and tried to boot from my ssd.  Needless to say it failed miserably and now i can't use my mini without a LiveUSB.  I have no idea what to do.  My mini9 is useless at this point.

Can anyone offer some help?

---

### Post by Xiong Chiamiov on 2009-02-28
UNR?

Fixing the partitioning problems will probably fix whatever issue you're having now.  It would be useful to have the error messages you got when partitioning, as well as the ones you get when you try to boot.

---

### Post by dasunst3r on 2009-02-28
UNR = Ubuntu Netbook Remix.  I would like to see what error messages you got as well.

---

### Post by gerz85 on 2009-02-28
UNR = Ubuntu Netbook Remix.  Using the remix on ubuntu 8.10 required me to stop Compiz from booting automatically with UNR.  So i had to turn it off using this guide: [http://www.ubuntumini.com/2008/11/stop-compiz-fusion-from-loading.html](http://www.ubuntumini.com/2008/11/stop-compiz-fusion-from-loading.html)

needless to say, i tried to reverse that step (changing it back to /usr/bin/compiz but it didnt work.  so i thought a fresh install would fix all that, but it just gave me more problems.

when going through the installation, it brought me to the partition set up the first time around, i deleted my previous partitions.  but now i seem to have partitions on top of that.

this is the guide i'm using: [http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html](http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html)

  I'm setting it up now and it says "file system has errors! you should run e2fsck."

---

### Post by Xiong Chiamiov on 2009-02-28
At which point in the process does it say that?

---

### Post by gerz85 on 2009-02-28
this error comes up after i create two new partitions

/dev/sda1 ext mount /
/dev/sda2 ext mount /home

---

