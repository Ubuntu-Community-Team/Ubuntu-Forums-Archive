---
title: "Went back to Ubuntu 9.1 because of auto features."
date: 2010-05-18
forum: New to Ubuntu
---

### Post by Bruce W on 2010-05-18
Hello:  I am learning from scratch about Linux.

I want to post my experience so far.

My first Linux was Ubuntu 9.1.  When it was installing, it asked me if I wanted to be given the choice at Boot Up of my Windows partition or this new Ubuntu partition.  After it was installed, I couldn't run some videos off the net, so it asked me if I wanted Ubuntu to download all needed files and install them.  I said 'Yes" and within seconds, I could run my videos.

I thought I was ready to learn more about my 64 bit motherboard, so I un-installed Ubuntu 9.1 and downloaded a heavy 64 bit OS called SUSE 11.2.  It took 11.5 hours to download as an ISO file and I burnt it to a DVD formated CD.  After installing, I did not have a boot choice of OS.  The computer only started in Linux.  I had to learn about the 'Boot' menu and how to request a Boot-Up choice.  That worked, but I spent hours trying to download patches (which never started) to get videos working.  Never happened.  I gave up and decided to to back to something I knew worked.  Ubuntu.

I tried the 64 bit Ubuntu 10.04.  It also did not give me a choice during the install of booting up in Windows or Linux.  Also, I spent hours trying to figure out how to get patches to make the video work.  I gave up and un-installed it.

Finally I went back to my Ubuntu 9.1.  (I don't know if it is designed for 32 & 64 bit?)  It was refreshing to see, during the install, it ask me whether I wanted a Boot-Up choice of Windows or Linux.  Also, as soon as I tried a video, it came back with a window to help me get patches.  I only clicked on one 'Yes' or 'Continue' and then 'BOOM', the video I was trying to run off the net started running.

I am confused as to why the later versions of Linux became more complicated.  Why not at least leave in the features that are suppose to make Linux simple and all-knowing.  At least now, I am back in action.

---

### Post by Chesamo on 2010-05-18
Get back into Ubuntu 10.04 and run sudo update-grub. It'll put Windows back on the boot list.

To get your videos working, sudo apt-get install ubuntu-restricted-extras.

Also, it's Ubuntu 9.10, not Ubuntu 9.1. The numbers are significant.

---

### Post by Bruce W on 2010-05-18
I forgot to mention: I loaded Windows 7 first.  Then Ubuntu.  It seems that if you load Ubuntu first, Windows 7 wants to eat up Ubuntu.

Experienced people will probably know how to solve this problem of installing Windows after Ubuntu, but for someone like me just starting, this is how I solved that problem.

---

### Post by Chesamo on 2010-05-18
Yes, Windows should be installed before Ubuntu. Simply because the Windows bootloader can't handle non-Windows OSs.

---

