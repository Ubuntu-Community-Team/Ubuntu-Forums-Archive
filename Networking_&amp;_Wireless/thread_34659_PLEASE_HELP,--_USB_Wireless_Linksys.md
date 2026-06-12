---
title: "PLEASE HELP,-- USB Wireless Linksys"
date: 2005-05-15
forum: Networking &amp; Wireless
---

### Post by Fuzzhead on 2005-05-15
Hi

I am new to linux, and would like to use ubuntu. I can run it from the 
Live CD, and it works well. However, I can not get the wireless
network installed and functioning.  Yes, I have run other posts, but
get lost in much of the techno speak that assumes familiarity with 
linux commands, etc.

I've tried below, but the "cvs ..."  generates a command not known error.
I can mount the drives, and read them from the root-terminal windows.

I think I have two options:
1. Obtain an AMD64-bit linux driver the device, but doubt one exists, 
can 't find one on Linksys site either.
2. Locate the windows driver files, and use ndiswrapper.

I think I should do option 2, but don't have ndiswrapper, do I with LiveCD version? And need to know the names for the window drivers files.  Would you please help me?  

Thanks, Michael



============================================
# sudo apt-get install build-essential linux-headers-`uname -r`
tar xzvf at76c503a-cvsroot.tar.gz
mv at76c503a CVS
cvs -d `pwd`/CVS co at76c503a
cd at76c503a
make
make install

---

### Post by Fuzzhead on 2005-05-15
btw  
I have the following setup
ubuntu 64bit version, LiveCD
AMD Athlon64 3000+, 
Linksys USB WUSB11 wireless device
1 gig ram
DVD rom
SonyDVD writier.
ViewSonic CP171s flat-panel monitor
USB mouse

---

### Post by Fuzzhead on 2005-05-17
I used a non-64 live CD, but couldn't get my wireless adapter to work.

I don't have an internet connection, so how do I do an "apt-get"?

There's no ndiswrapper within Ubuntu, and I don't know how to 
get the correct version for my system.  I think I need to download
a bunch of stuff, and compile code, and do a bunch of steps in
a certain order.  Is this the case?

imho, Linux isn't going ANYWHERE until there's better hardware support
and easy tools to get up and running.  Ubuntu does a pretty good
job, and I like the LiveCDs. However, Ubuntu doesn't recognize my
network card on an old system, where as another Distro does. Ugh!@
</venting>

I'll get off my soap box now. But PLEASE, someone help, please!!!

Thanks,
Michael

---

