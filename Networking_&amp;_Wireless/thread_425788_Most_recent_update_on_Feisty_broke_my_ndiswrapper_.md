---
title: "Most recent update on Feisty broke my ndiswrapper wireless"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by jac1d on 2007-04-27
I'm running 7.04 feisty on an Acer 3050 laptop.  It has the irritating Broadcom bcm4318 airforce one chip for wifi.

I was successfully using the ndiswrapper and the driver ACER supplies (thoughtfully in c:\windows\802bg) for the last few weeks.  I was using the network manager applet to connect to my home WEP network (and had my wep key on my keyring).

Everything was fine... I started up tonight to add a few things to my desktop and it said there were updates (I had the PC off for about 2 days).  I installed them and my wifi stopped working.

I reinstalled 7.04 from scratch from the ISO (but left home alone).  I did the full updates available first, and then installed ndiswrapper and set up my driver again.

I blacklisted the native driver in /etc/modprobe.d/blacklist:

# Broadcom 4318 driver (native)
blacklist bcm43xx

I installed ndiswrapper with apt-get and then I loaded in the inf I was using previously (I copied the whole driver directory off my windows partition and put it under home).

root@tech-laptop:/home/tech# ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)

The driver appears to be loaded a,s before but now I can't scan or get any life out of it.  If I boot back in to Windows XP MCE the wireless works fine, so its not hardware.

Now, previously my wireless would show up as wlan0 in ifconfig.  Now it is showing as eth1.  This shouldn't make any difference but may offer a clue as to what happened.  Also, I'm getting this avahi stuff, which I am not familiar with:

ifconfig eth1

eth1      Link encap:Ethernet  HWaddr 00:16:CF:CB:E8:6F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Memory:d0200000-d0202000 

eth1:avah Link encap:Ethernet  HWaddr 00:16:CF:CB:E8:6F  
          inet addr:169.254.9.225  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Memory:d0200000-d0202000 

Can anyone help me get this back online? 

Thanks

-Jeff

---

### Post by jac1d on 2007-04-27
I don't know enough about Avahi yet but it appears to be the source of the problem from what I can glean from other posts.  How do I banish this thing or do I want/need to get rid of it to get my wireless back?  Also, where/when did my beloved and working wlan0 become eth1?

-Jeff

---

### Post by jac1d on 2007-04-27
Ok, this is highly unusual... I've fixed it but I'm not quite sure how.

For background, or for other people who want easy, short, straightforward docs on how to install your BCM4318, I used this info:

[http://wiki.linuxquestions.org/wiki/Broadcom_4318_Airforce_one_54g_card](http://wiki.linuxquestions.org/wiki/Broadcom_4318_Airforce_one_54g_card)

I redid all that just now so things were clean.  Nothing worked, could not scan or connect.  Then I went in to the network appelet and manually told it the ESSID of my home network.  That seemed to make things spring to life and it suddenly "saw" my neighbours network as well.  Better still it recognized it still had my WEP key on my keyring (when I reinstalled I left /home in tact).  And up I came.

I rebooted, and got the complaint that netif couldn't change wlan0, which is what I *used* tog get at boot, and low and behold wlan0 is back and I am writing this via wireless.

Something very strange in that last update, its a shame this had to happen.  I was having such a smooth experience with 7.04 up until now.

-Jeff

---

### Post by jasonbrisbane on 2007-04-28
Well, I found out that you dont need ndiswrapper with Fiesty.

With a wired network,  search synaptic for bcm43xx-cutter and download and say yes to everything.
Reboot and hey presto!

---

### Post by cari on 2007-07-21
I did the same update on edgy and now network-admin fails to show my wireless device (trendnet TEW-423PI)
although:
```

ndiswrapper -l

```
shows
```

mrv8000c : driver installed
device (11AB:1FAA) present

```
Also I'm unable to scan for available networks (no wlan device whatsoever). Could it be that my wlan became eth0 also?

TY in advance for any help

EDIT: everything works fine with previous kernel (11), but as soon as I boot up with next build (12) my wireless stops working

---

