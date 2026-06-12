---
title: "help with zonet zew2501 linux driver"
date: 2006-09-23
forum: Networking &amp; Wireless
---

### Post by joeisanemokid on 2006-09-23
I am quite new with ubuntu, and have installed it on a spare computer, now I am trying to get that computer onto my wireless network. I thought that by buying a usb wireless adapter with linux drivers i could bypass the wireless issue many people seem to have. However, the documentation for the driver is slightly confusing for me. I have already tried using ndiswrapper, and have installed the windows xp driver, but afterwards the "networking" program still didnt regognize any wireless devices, nor did iwconfig or ifconfig.  

Now all i am asking is for someone to give me a slightly easier explanation of how on earth to use this driver, your help is GREATLY appreciated, i would really love to resolve this issue so as to keep using and learning ubuntu.

if any additional information is needed, just reply or email me at [email]joeisanemokid@gmail.com[/email]

2.2 Build and install the package:
The package contains drivers for ZD1211 and ZD1211B. If you doesn’t have specified
request, both of them will be installed.
Under the extracted directory, there is a Makefile in it. Because our driver can support for
kernel 2.4 and kernel 2.6, there are two sets of rule in the Makefile. One has to modify
the Makefile according to the path of “kernel source tree” and the version of the kernel
in your system. In the Makefile, you may see the following statements,
# if the kernel is 2.6.x, turn on this
#KERN_26=y
#KERNEL_SOURCE=/usr/src/linux-2.6.7
# if the kernel is 2.4.x, turn on this
KERN_24=y
KERNEL_SOURCE=/usr/src/linux-2.4.20-8
If you want to build the kernel under the kernel of 2.4.x, one has to let the variable
KERN_24=y and comment the KERN_26=y like that as the example above and modify
the variable KERNEL_SOURCE to the path which you install the kernel source. After
doing these things, one just need to type the “make”, and the driver module will be
generated and installed.

---

### Post by tetraminoe on 2006-09-26
I am also new to Linux, but I managed to get this to work (after some wrangling).

I have the [Zonet ZEW2501]("http://www.zonetusa.com/DispProduct.asp?ProductID=152") USB wireless adapter and am running Ubuntu Dapper Drake 6.06. These instructions worked from a fresh install so you should be good right off the CD.

Go into Synaptic and search for **linux-headers** in Name. I don't know exactly what you need here, so I just get everything. You can exclude some stuff that may obviously be irrelevant, e.g. server.

Go to Terminal and type **sudo apt-get install build-essential**. When prompted for your password, enter it.

Go to [http://zd1211.ath.cx/](http://zd1211.ath.cx/) and download the latest driver. These instructions worked with r83.

Untar the driver.

Open **Makefile** in Gedit and find the line that includes **ZD1211REV_B=0**. Change that to **ZD1211REV_B=1**.

In the terminal, go to the directory where you untarred the driver. Type **make**.

When that is done, type **sudo make install**.

Type **sudo modprobe -v zd1211b**.

Type **lsmod | grep zd**. It should show a result for zd1211b.

Type **sudo ifconfig wlan0 up**.

Type **sudo iwconfig wlan0 essid *youressid***, where *youressid* is the name of the wireless network to which you are trying to connect. (Alternatively, you should be able to open the Networking menu and select the network there. Enter your password if needed.)

Type **sudo dhclient wlan0**.

Try **ping [www.google.com](www.google.com)** and hope it works :) 

Good luck!

---

### Post by joeisanemokid on 2006-10-01
Thank you, I have managed to install the driver. Network settings recognized the hardware and I can see the networks available to me, but still cannot manage to connect to mine, even after temporarily unencrypting it. I know it is not an issue between my router and the zonet because I already tried it with my computer that still runs xp. 

Your instructions worked great but I dont know where to turn now to resolve the current problem. On the brighter side hopefully people with similar problems can read this thread and solve them.

---

### Post by AscendedDaniel on 2006-11-01
I tried this, except that at the step **sudo ifconfig wlan0 up** I get the following message: "wlan0: ERROR while getting interface flags: No such device". Any help or resources you can offer would be appreciated. Thanks.

---

### Post by jrevillini on 2007-08-14
fisrt, i'm not very conversant in linux terminology.  i'm a web application developer, so take that for what it's worth...

for those of you who installed the 2.6.22-x kernel (mine is 2.6.22-9), you are probably having trouble with the make file.  as in, you get beaucoup errors and then you can not install the driver.

i had to following many disparate pieces of information, but I finally arrived at this procedure.  i hope it works for you as well.

0. you should probably go into your temp directory to get started.  at the command line.

**cd /tmp**

You also need to create this file which the new kernel does not have (I'm not saying this is the *right* way to do it, but it's a way to do it (source: [http://www.labjack.com/forums/index.php?s=&showtopic=1623&view=findpost&p=6096](http://www.labjack.com/forums/index.php?s=&showtopic=1623&view=findpost&p=6096)).

**sudo gedit /lib/modules/*YOUR_KERNEL_DIR*/build/include/linux/config.h**, where *YOUR_KERNEL_DIR* is the 2.6.22-x kernel directory (example: 2.6.22-9-generic)

Paste this:

```

#ifndef _LINUX_CONFIG_H
#define _LINUX_CONFIG_H
/* This file is no longer in use and kept only for backward compatibility.
 * autoconf.h is now included via -imacros on the commandline
 */
#include <linux/autoconf.h>

#endif

```

Save the file.  Now we can begin...

1. instead of following the download link for the driver above, check out the latest from SVN by typing this at the command line (source: [http://ubuntuforums.org/showpost.php?p=2899830&postcount=4](http://ubuntuforums.org/showpost.php?p=2899830&postcount=4)):

**svn export [https://zd1211.svn.sourceforge.net/svnroot/zd1211/trunk](https://zd1211.svn.sourceforge.net/svnroot/zd1211/trunk) zd1211**

2. now cd into that new directory you just pulled stuff into like so:

**cd zd1211**

3. if you're lucky, that checkout grabbed the latest community maintained stuff, and it has the latest patches applied.  so at this point, you're going to *try* to do the make now.  now instead of just typing 'make' and instead of editing the makefile, you can just include the flag they're talking about on the command line like this (source: [https://answers.launchpad.net/ubuntu/+question/11119](https://answers.launchpad.net/ubuntu/+question/11119)):

**sudo make ZD1211REV_B=1**

4. Check the output.  Did it LEAVE because of an ERROR, or did it take awhile and compile a bunch of stuff?  If it compiled, you can skip step 5.

5. OK, so, like me, it didn't work yet.  Well, luckily for us, a nice spanish-speaking lad out there waded through a lot of code and information and figured out 2 key lines in the file which need to be changed to work with the 2.6.22 kernel.  your checkout grabbed code that only works up to the 2.6.20 kernel (probably).  What you want to do is (source: [http://sourceforge.net/mailarchive/message.php?msg_name=200708050148.02646.ftoledo%40docksud.com.ar](http://sourceforge.net/mailarchive/message.php?msg_name=200708050148.02646.ftoledo%40docksud.com.ar)):

**sudo gedit src/zd1205.c**

And then go to line 4159 and comment it out by changing it to 

```
//skb->mac.raw = skb->data;
```

And then go to line 4780 and change it to

```
struct iw_statistics *iw_stats = &macp->device->stats;
```

And then save it.  Now go back and repeat step 3 and 4.

6. OK, we should all have a valid build of the whatever now.  We can now install it like this:

**sudo make ZD1211REV_B=1 install**

7.  Now, you can just pick up in the instructions that tetraminoe gave us, which I'll quote here just to save you a bit of scrolling

> Type **sudo modprobe -v zd1211b**.

Type **lsmod | grep zd**. It should show a result for zd1211b.

Type **sudo ifconfig wlan0 up**.

Type **sudo iwconfig wlan0 essid *youressid***, where *youressid* is the name of the wireless network to which you are trying to connect. (Alternatively, you should be able to open the Networking menu and select the network there. Enter your password if needed.)

Type **sudo dhclient wlan0**.

Try **ping [www.google.com](www.google.com)** and hope it works 


I feel pretty good about myself ... I've never actually troubleshot something of this nature before, and I feel like I've learned a few things about the system, even though I don't fully understand what I've learned nor how to explain it that well to others.  still, it goes to show that with some time on your hands and the willingness to google the sh*t out of a problem, sometimes you can follow a trail of information just far enough to fix something.

i sincerely hope that at least one person gets an up and running usb wifi device as a result of this guide.

---

