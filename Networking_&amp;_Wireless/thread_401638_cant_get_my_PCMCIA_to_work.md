---
title: "cant get my PCMCIA to work"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by smokiedbest on 2007-04-04
Hello, i am new to Ubuntu. i am trying to get my ZTE MG 166 PCMCIA modem. i have gone through the posts, and as i am new to Ubuntu (and Linux), i really cant figure out some of what is being said. Also someone mentioned that ZTE modems cant work   on linux. Please is it true, if not, can i get a step by step account of how i can get it to work.

Thanx in advance<br /><br />
----------------------------------------<br />

----------------------------------------<br />

---

### Post by SoggyCornflake on 2007-04-04
> **smokiedbest said:**
> Hello, i am new to Ubuntu. i am trying to get my ZTE MG 166 PCMCIA modem. i have gone through the posts, and as i am new to Ubuntu (and Linux), i really cant figure out some of what is being said. Also someone mentioned that ZTE modems cant work   on linux. Please is it true, if not, can i get a step by step account of how i can get it to work.

Thanx in advance<br /><br />


Hello,

Always glad to help a Newbie - we were all newbies once.

First of all I am not sure if your hardware is supported out of the Box by Ubuntu.  You can start by checking this [Link to the Linux Hardware Compatibility HOWTO.]("http://www.tldp.org/HOWTO/Hardware-HOWTO/")  It may take a bit of reading on your part, but there's lots of good advice.

Perhaps you've heard of "Winmodems"   When computer manufacturers tried to design cheaper computers, the decided to emulate serial modems in software.  These modems would work fine in Windows since the hardware manufacturers supplied the software drivers to make them work.  Linux worked great on older - real serial - modems but since the hardware manufacturers didn't supply Linux drivers for their win-modem products they were at one time pretty useless for Linux users.  Over time some clever programmers figured out how to emulate certain brands of Winwodems. (Usually by the Chips used by the modem).  That means once useless Winmodems may now be used in LInux on a case by case basis.

Just because it can be used in Linux doesn't mean a distro will work with it out of the box.    You may need to add a module to the kernal to get it to work.

One way to see if your pcmcia device is being seen correctly by your Linux kernel is to  do the following: 

```
lspcmcia
```
This will list all the PCMICA devices on your system.  it will probably give you enough info to get lots of help.

Another useful command to type prior to plugging in your PCMCIA device, open a terminal session and type the following:

```
lsmod >File1.txt
```
Then insert the PCMCIA modem and type
```
lsmod >File2.txt
```

Open up these two text files with your favorite editor and compare them.  They should be basically the same, but the second one may have a new module(s) listed.

Assuming the kernel found your PCMCIA modem and has a kernal module for it, then typing lsmod <--stands for list modules  -- will show the module it uses for that modem.  If there is no difference then you've probably got some research to do.

Once you do those two things you'll be armed with information.  If you can't figure it out from that, there's lots of people here who thrive on helping.  Although I don't have any PCMCIA experiance with Ubuntu, somebody following up this thread no doubt will.

---

