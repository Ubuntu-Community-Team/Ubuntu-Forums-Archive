---
title: "Ubuntu 9.10 alpha 6 Wubi install doesn't work, goes to bash"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by db4sn3r on 2009-09-19
Hi,

I installed ubuntu 9.10 alpha 6 on my samsung nc10 netbook in windows 7 RC.  I downloaded the x86 ISO for it and opened it with wubi.  The installation looked like it was doing well.  I rebooted, and the ubuntu button was there.  I booted into it, completed the rest of the installation, and then rebooted to actually test the thing out.  I hit the ubuntu button, and it went straight to a bash interface.  I really want this to work because the last time I tried to partition something myself, I messed up my computer.  should I just try the wubi install again? different version of wubi? bash commands? please help!

Thanks,
db4sn3r

---

### Post by anewguy on 2009-09-19
I have always had either a straight install of Ubuntu, or Ubunut in a vm, so I'm not familiar with using wubi, but as I understand it, it is just Ubuntu installed in a file in Windows, and you click the Ubuntu button you actually boot to it.  There is also a netbook remix version of Ubuntu available for download straight from Ubuntu, and this may be your best option to try either in wubi or as a straight install, as it is tailored for netbooks.

That being said, if it is normal Ubuntu, it sounds like the X server is either not being started, or it fails because of the video driver - both of these would cause you to go to the command line instead of a windowed environment.

To see if the X server is just not starting, at the command line type:

startx <press enter>

Wait and see if a window comes up - if not, and you end up back at the command line, then chances are that the video driver you need is not installed.  To double check that, type:

cat Xorg.0.log <press enter>

You will be able to scroll the output up and down - look for things with three starts (***) as these are the fatals to X.  Copy the output and post them back here.

Also do the following:

lspci <press enter>

Copy the output and post back here.  The lspci command tells Ubuntu to list all of it's PCI interface devices.  Most video cards use this interface.

We'll go from there once you post back.  Also - what is the make/model of the PC?

Dave :)

---

### Post by W2IBC on 2009-09-19
also remember 9.10 is a alpha and is prone to breakage.

i would try 9.04 as it is the stable release.

---

### Post by raha on 2009-10-03
I also had a problem with installing Ubuntu 9.10 Beta using wubi on my Windows 7 beta.

Everything goes well and you get a message "Everything was successful" but when I restart and select Ubuntu I get an error saying wubivm (or something like that) could not be found.

---

### Post by TheReg on 2009-10-24
> **raha said:**
> I also had a problem with installing Ubuntu 9.10 Beta using wubi on my Windows 7 beta.

Everything goes well and you get a message "Everything was successful" but when I restart and select Ubuntu I get an error saying wubivm (or something like that) could not be found.

I believe the problem is simply rooted within Ubuntu Beta code IN a Windows 7 beta environment.

I know this is of no real help. But step back and think for a minute what it is you are doing and what could you actually expect to happen.

---

