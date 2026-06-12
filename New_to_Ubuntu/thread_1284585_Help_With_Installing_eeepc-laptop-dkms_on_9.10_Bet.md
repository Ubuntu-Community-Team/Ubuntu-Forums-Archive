---
title: "Help With Installing eeepc-laptop-dkms on 9.10 Beta Netbook Remix"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by APer3Caper on 2009-10-06
After many years of tinkering with Linux and Ubuntu, I've finally decided to use as my primary OS on my one of my computers. I swore that whatever problem I encountered I would do whatever it take to find a solution and I would not reinstall Windows. 
So, my first question involves the installation of eeepc-laptop-dkms. I've been following a guide on installing Ubuntu 9.04 Netbook Remix on the Eee PC 1005HA (my computer) that I found here: [http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/]("http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/"). Except, I decided to use Ubuntu 9.10 Beta Netbook Remix instead of 9.04 since WiFi and Ethernet work out of the box with 9.10. I went through most of the guide perfectly fine until I encountered the portion about setting up the Super Hybrid Engine and Eee PC tray. I added the repository that the author listed (the Karmic version of the repo though) and installed the packages he directed. eeepc-tray installed fine and appears to be working, however when I try to install eeepc-laptop-dkms this error message appears:
```
E: eeepc-laptop-dkms: subprocess installed post-installation script returned error exit status 10
```
[INDENT][/INDENT]Synaptic shows that the package is installed but the error continues to pop up whenever I install or update anything. I've reinstalled the package, I've completely removed the package and then installed it again, but the error persists. 
[INDENT][/INDENT]I hope that some of you wise Ubuntu gurus could weigh in on this issue and provide me with the assistance I need. Thank you.

---

### Post by mikeyphi on 2009-10-07
This might help......

Open a terminal and enter the following:
sudo dpkg --configure -a


Then enter your password when requested

---

### Post by ViRMiN on 2009-10-07
I've got the same issue with a 1000HE model.  Google, being my friend, brought me to your thread! lol

---

### Post by APer3Caper on 2009-10-07
I entered that command as you instructed and I'm not so sure it worked.
Here's what came up:
```
user@Computer:~$ sudo dpkg --configure -a
[sudo] password for user: 
Setting up eeepc-laptop-dkms (0.1) ...
Removing old eeepc-laptop-0.1 DKMS files...

------------------------------
Deleting module version: 0.1
completely from the DKMS tree.
------------------------------
Done.
Loading new eeepc-laptop-0.1 DKMS files...

Loading tarball for module: eeepc-laptop / version: 0.1

Loading /usr/src/eeepc-laptop-0.1...
Creating /var/lib/dkms/eeepc-laptop/0.1/source symlink...

DKMS: ldtarball Completed.
Installing prebuilt kernel module binaries (if any)
Building module...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
su nobody -c "make KERNELRELEASE=2.6.31-12-generic"....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.31-12-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/eeepc-laptop/0.1/build/ for more information.
0
0
dpkg: error processing eeepc-laptop-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 eeepc-laptop-dkms
```

---

### Post by mikeyphi on 2009-10-07
It looks as though the problem lies with the kernel used. Probably by using 9.10 when the other packages are designed for 9.4

You could do a search to see if anyone has updated the procedure using 9.10

otherwise you might have to revert to 9.4

---

### Post by APer3Caper on 2009-10-09
I went to [this website]("http://www.statux.org/content?page=repo") for instructions on settings up the repo. I selected the one for Karmic but now it appears that repo is gone and the one for Jaunty remains. Well, I uninstalled the package, the problem went away, and it doens't appear I need it anyway. Thanks for all the help though. If anyone else has any ideas feel free to drop them here.

---

### Post by ViRMiN on 2009-10-10
Did you see the blog posting?  [http://www.fewt.com/2009/10/i-give-up.html](http://www.fewt.com/2009/10/i-give-up.html)

---

### Post by t0p on 2009-10-10
Have you thought of just installing Eeebuntu? I messed around with Ubuntu Netbook Remix in the past, but using Eeebuntu was the best option.

---

### Post by fewt on 2009-10-14
> **APer3Caper said:**
> After many years of tinkering with Linux and Ubuntu, I've finally decided to use as my primary OS on my one of my computers. I swore that whatever problem I encountered I would do whatever it take to find a solution and I would not reinstall Windows. 
So, my first question involves the installation of eeepc-laptop-dkms. I've been following a guide on installing Ubuntu 9.04 Netbook Remix on the Eee PC 1005HA (my computer) that I found here: [http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/]("http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/"). Except, I decided to use Ubuntu 9.10 Beta Netbook Remix instead of 9.04 since WiFi and Ethernet work out of the box with 9.10. I went through most of the guide perfectly fine until I encountered the portion about setting up the Super Hybrid Engine and Eee PC tray. I added the repository that the author listed (the Karmic version of the repo though) and installed the packages he directed. eeepc-tray installed fine and appears to be working, however when I try to install eeepc-laptop-dkms this error message appears:
```
E: eeepc-laptop-dkms: subprocess installed post-installation script returned error exit status 10
```
[INDENT][/INDENT]Synaptic shows that the package is installed but the error continues to pop up whenever I install or update anything. I've reinstalled the package, I've completely removed the package and then installed it again, but the error persists. 
[INDENT][/INDENT]I hope that some of you wise Ubuntu gurus could weigh in on this issue and provide me with the assistance I need. Thank you.

It is no longer necessary to install this in Karmic.

---

### Post by gopal on 2009-10-31
Fewt,

Thank you for confirming this. 
I had this problem and didn't know how to proceed.

I will be in remiss if I did not say how much I appreciate your diligent efforts to update the package!! Thank you!

---

### Post by fewt on 2009-11-02
> **gopal said:**
> Fewt,

Thank you for confirming this. 
I had this problem and didn't know how to proceed.

I will be in remiss if I did not say how much I appreciate your diligent efforts to update the package!! Thank you!

Welcome.

---

