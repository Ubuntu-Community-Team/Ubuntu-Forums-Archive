---
title: "How to install Ndiswrapper"
date: 2013-09-12
forum: Networking &amp; Wireless
---

### Post by john102 on 2013-09-12
I just recently installed ubuntu 12.04 and I have the wireless usb AE2500 and it is not supported by ubuntu, I have tried for about 3 hours on installing the program for it.
I copied the .tar file onto a usb and then moved it to the ubuntu desktop then after that I am at a loss.

---

### Post by verymadpip on 2013-09-12
Hi there.
Before going down the ndiswrapper route is there a proprietary linux driver from the device's maker available?  (It seems not).

To install ndiswrapper:
Right click on the .tar  & select extract here.
Open the shiny new folder that process made.
Look for a file named "INSTALL" which explains how to install ndiswrapper.
Open that up with a text editor & follow the instructions.

If that all works we can try installing drivers.

I'm not sure of the state of 64 bit XP drivers, or if they even exist, so you may need to run a 32 bit OS for this to work.

---

### Post by coffeecat on 2013-09-12
> **john102 said:**
> 
I copied the .tar file onto a usb and then moved it to the ubuntu desktop

Have you tried installing the repository version of ndiswrapper from Software Centre? Why did you download a tar file? Was this a howto you were following?

You might want to read this thread:

[http://ubuntuforums.org/showthread.php?t=1805830](http://ubuntuforums.org/showthread.php?t=1805830)

It seems you have the bad fortune to choose a problematic wireless chipset.

---

### Post by john102 on 2013-09-13
I recently installed Ubuntu 12.04LTS 64 bit recently and I need to connect to the internet but the problem is that I can't. I downloaded ndiswrapper 1.58 tar.gz and put it on a thumb driver and moved it over to ubuntu and it tells me to install it by opening terminal and inputting

tar zxvf ndiswrapper-1.58.tar gz

and it tells me error message no such file or directory. Can I get a little help please because I am very interested in using Ubuntu.

---

### Post by john102 on 2013-09-13
Well when I go to the software center there is no option to download ndiswrapper is the problem. Do you think I should install the 32-bit instead?

---

### Post by verymadpip on 2013-09-13
You need to be in the folder you saved the .tar.gz file to.
For example, I save mine to my Downloads folder so I would opoen a terminal & enter:

```
cd Downloads
```

If the file is on your desktop then replace Downloads with Desktop or wherever it is.

Then run the untar command.

Alternatively, right click on the .tar.gz file & select extract here.
At this point find the "INSTALL" file in the extracted folder & follow the instructions on how to install.

You seem to have 2 threads dealing with this, which is confusing the heck out of me.
Relating to your other thread:  Ndiswrapper shows up in software centre as Windows Wireless Drivers & it's in my Xubuntu 12.04 & 13.04 Software Centre.
I have had more success with the downloaded file which you already have.

---

### Post by Jonathan Precise on 2013-09-13
Please do not post [duplicates]("http://ubuntuforums.org/showthread.php?t=2174211"). It dilutes the community effort.

---

### Post by mörgæs on 2013-09-13
Threads merged.

---

### Post by john102 on 2013-09-13
Sorry about the two threads and sorry i know I am a total newbie when it comes to this but I did the the cd Desktop and I ran the tar extractor and it said the same thing, no such file or directory. I'm sorry guys I am still learning

---

### Post by praseodym on 2013-09-13
Hi,

which kernel do you use? Please show
```

uname -a
```

---

### Post by john102 on 2013-09-13
I got to extract it and when I did make install it gave me an error message...and I am using 3.8.0-29-generic

---

### Post by verymadpip on 2013-09-14
Hi again.
What's the error message?
You may need to install build-essential & dkms.
Have you read the thread linked by coffeecat in post #3? *That's all about your adapter*.

If I recall correctly, there was a time when Ndiswrapper issues with the repository version were cured by also installing ndiswrapper-dkms.  If that's still the case I don't know, I seem to remember it stopped working.

Personally I was using checkinstall (which needs to be installed) instead of make install.  I think there's some healthy debate about that, but what the heck.

---

### Post by s-bodet on 2013-09-14
Hi,

I've been struggling against the AE2500 as well :-(

The post here after

[http://ubuntuforums.org/showthread.php?t=1805830&p=11811107#post11811107](http://ubuntuforums.org/showthread.php?t=1805830&p=11811107#post11811107)

was my starting point...


Personnally, the best I was able to do was to have it up and running with no security.  When trying to gain access to a WPA network, the network manager kept asking for the PSK.  I read a lot of stuff onto this type of issue but I have not been able to fix my problem.

BTW, that was on a notebook running Saucy Salamander.  I'll wait for a few software updates to redo my testings.

Steve

---

