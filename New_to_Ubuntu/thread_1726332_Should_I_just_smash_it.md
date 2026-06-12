---
title: "Should I just smash it?"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by tysonh80 on 2011-04-11
I have been trying to get my asus usb n13 wifi to work for almost a week now.  I have tried a lot of the how to's on installing this thing but haven't met with any luck yet.  I downloaded the latest driver and when I attempt type make into terminal in the correct directory it looks like its building it until it stops and says error code 2.

Strange thing is that the I can see my wifi card in iwlist.  Its identifies it has Ralink RT 2870 STA.  It even says im connected to my network.  But as soon as I try to load a page the connection drops.  The first time I plugged in the card.  I tested the download speed and it returned up to 5mbs.  Now if I can even load the page it returns a awesome .25mbs or drops the connection before the test can complete.  

I've tried reinstalling several times following different guides on the forums.  I've even tried installing different earlier releases of ubuntu.  I currently using 10.10.  I've tried 10.04 and I think its 9.10 that I have as well.

My question is this.  Given that my system knows the wifi card is plugged in and it connects to my network.  Am I missing something stupid that is preventing me from achieving wireless N speeds or at the very least a stable connection?  Any help would  be well received.

---

### Post by tysonh80 on 2011-04-11
when I try the make command to goes until this happens:

/home/war/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1510: error: ‘struct net_device’ has no member named ‘open’
/home/war/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1511: error: ‘struct net_device’ has no member named ‘stop’
/home/war/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1512: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/war/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1513: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/war/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1519: error: ‘struct net_device’ has no member named ‘get_stats’
/home/war/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1553: error: ‘struct net_device’ has no member named ‘validate_addr’
make[2]: *** [/home/war/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/war/Downloads/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux] Error 2

---

### Post by Rasa1111 on 2011-04-11
I am assuming that you have first tried "additional drivers"? 
In the System>Admin menu? 

 Usually there will be a couple different ones to choose from.
and usually , in my experience.., only one of them works. 

Sorry if you already tried this. 

Good luck. <3

---

### Post by dcsoldschool53 on 2011-04-11
[B]I am not sure if your device is compatible with Ubuntu. Check and see if it is first before we go through the trouble of fixing it.
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
[/B]

---

### Post by wep940 on 2011-04-11
It may be as simple as blacklisting a module.  See the following link for more information on getting your adapter working in Ubuntu:
 
[http://linuxforums.org.uk/hardware-compatibility/ralink-rt2870-based-usb-wireless-n-adapters-(ubuntu)/](http://linuxforums.org.uk/hardware-compatibility/ralink-rt2870-based-usb-wireless-n-adapters-(ubuntu)/)

---

