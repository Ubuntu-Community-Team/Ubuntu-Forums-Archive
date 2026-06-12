---
title: "Ndiswrapper Problem after upgrade to Gusty"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by Dgood on 2007-11-01
I'll start by stating what my problem is.
Problem: After installing Ubuntu 7.10 Gusty I downloaded (with ethernet connection) the windows wireless drivers ndiswrapper. I did this because I prefer the graphical interface to memorizing the order of commands to type in. I ran the ndiswrapper as I had in 7.04, and it immediately froze. Upon trying this multiple times, i decided to try the ndiswrapper via the console. It froze each time doing that. 

That is the primary problem. Ndiswrapper that worked in previous version with my wireless card now doesn't. Now I now I have an odd wireless card. Dlink Dwa 552 pci wireless N card. It did work on previous versions of ubuntu and kubuntu with the ndiswrappers. 

The other problem was after I tried a different fix after assigning the driver to the specific hardware number xxxx:xxxx it said the driver was set. The problem occurs after even giving that hardware the name wlan0. when you try to implement it. Trying to start the card or make it detectable (whatever that step is). It freezes at that point. If you try one of hte fixes I found online you use a different code at the end or you edit the interfaces.txt file. If you edit the interfaces file, ubuntu or kubuntu (neither) will boot. It just hangs on the boot.

To get down to it, I want to know what to do to get my driver to work like it used to on 7.04 on either ubuntu or kubuntu 7.10. I would prefer kubuntu as I want to demo with kde 4 beta 4, compiz fusion, and kiba dock. 

Thanks in advance. -Darin

---

### Post by Dgood on 2007-11-05
bump still having problems, any body got a thread to link me to at least?

---

### Post by kevdog on 2007-11-05
7.10 uses a different upgraded kernel version compared to 7.04, so any custom kernel module you installed (such as ndiswrapper), needs to be reinstalled.  Thats the story.

---

### Post by Dgood on 2007-11-06
I have reinstalled the entire operating system then downloaded the newest ndiswrapper 1.9 and then tried to use it. I have done this multiple times as I had permanently locked the system up. I just want to know the trick to using a windows driver to make my wireless card work in gusty. I know there is a new kernel, how can I make it work with that new kernel. Thanks.

---

### Post by Dgood on 2007-11-09
Bump

---

### Post by kevdog on 2007-11-09
You need to provide some more details since you are giving me nothing to work with.  How about lets start with the basics

lspci -nn
lshw -C network
ndiswrapper -v
ndiswrapper -l

---

### Post by Dgood on 2007-11-10
01:07.0 Network controller: Atheros Communications, Inc. AR5416 802.11a/b/g/n Wireless PCI Adapter (rev 01)
01:07.0 0280: 168c:0023 (rev 01)

---

### Post by Dgood on 2007-11-10
*-network UNCLAIMED
             description: Network controller
             product: AR5416 802.11a/b/g/n Wireless PCI Adapter
             vendor: Atheros Communications, Inc.
             physical id: 7
             bus info: pci@0000:01:07.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: latency=32

darin@darin-desktop:~$ sudo ndiswrapper -l
net5416 : driver installed  device (168C:0023) present

darin@darin-desktop:~$ sudo ndiswrapper -v
utils version: 1.9
driver filename:  
    /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:      
  1.45
vermagic:       2.6.22-14-generic SMP mod_unload 586

---

### Post by kevdog on 2007-11-10
Where is your windows xp driver (or .inf and .sys file)?  You have installed anything inside ndiswrapper yet have you??

---

### Post by Dgood on 2007-11-10
I copied the .sys and .inf and .cab or whatever that I downloaded off of the dlink website into my /home/darin/Wireless folder. I then ran the ndiswrapper whatever version I have listed. Then I did the -i net5416.inf and then assigned it to the correct xxxx:xxxx device number. so yes, I did install it. then I set an alias to the device to wlan0. after that is where I screwed up. I don't know how to make Linux Use that device wlan0 and have it show up in my network. If I do modprobe thing, it freezes and if I add lines to my interfaces file it causes it to hang on boot and forces me to reinstall ubuntu to fix it.

---

### Post by kevdog on 2007-11-11
Only one driver is listed with ndiswrapper -l ???

And if you do sudo modprobe ndiswrapper the system freezes???  Are you running 32 or 64 bit Ubuntu??  Have you tried redownloading the drivers for your appropriate ubuntu version from the manufacture's website?

---

### Post by Dgood on 2007-11-11
32 bit as dlink only has 32 bit windows drivers for the card. And wireless N is not supported by Ubuntu yet. However as stated, I used the ndiswrapper with no problems on Fiesty. It was in gusty that the problems started. Whenever I try to actually implement the driver is when it locks up and I can't use the os anymore. That lock up usually results in the need for a reinstall such as currently. Luckily i'm dual booting.

---

### Post by kevdog on 2007-11-11
Ok, insert the driver inside ndiswrapper and then please post the results of 

ndiswrapper -l

 I want to make sure that this statement is correct before you load the ndiswrapper module into the kernel -- this is probably the part that you OS locks up.

---

### Post by Dgood on 2007-11-11
Ok before I do this can I get the commands you want me to do exactly as I will have to reinstall before I can do this. I want to make sure I don't do too much. 
I'll have the driver in a folder /home/darin/wireless
I'll install the ndiswrapper from the cd as I have no internet without the card. 
Then I'll type what?
cd /home/darin/Wireless
sudo ndiswrapper -i net5416.inf  (etc) what steps do I do and what do I not to?

---

### Post by kevdog on 2007-11-11
Use this link only as a guide -- you do not need to do every step since it seems you have ndiswrapper installed.  Just peruse the instructions and pick up things as you think appropriate:

[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

