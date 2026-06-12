---
title: "Live CD, no network at all."
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by xini on 2007-12-11
Help for a total newbie is needed. I am running Ubuntu from a live CD to try linux out.  Networking and Internet is not available at all.  The hardware seems to be detected (RTL 8139).  I have played around with the network settings trying, roaming, dhcp and setting it to a static address to my router (DL 504).  DEAD.   On windows xp everything works fine, when a Macs hooked up it works fine, 

So, the question is, has anyone any idea why ubuntu wont speak to my router?  When the lan cable is connected there is nothing, not even a flicker of light to indicate that the router has recognised an attached device (this happens with xp and mac) despite the tinkering with the different settings.

Since i'm a newbie, please keep it simple guys, I want to ditch the "gates mob" just as much as the next guy, but need to be gently nudged along  with some friendly support and advice which will be gratefully accepted.

The "buy this and that" brigade need not reply unless you post it to me for free (haha), i'm stuck in the back end of nowhere.

---

### Post by SoggyCornflake on 2007-12-11
> **xini said:**
> Help for a total newbie is needed. I am running Ubuntu from a live CD to try linux out.  Networking and Internet is not available at all.  The hardware seems to be detected (RTL 8139).  I have played around with the network settings trying, roaming, dhcp and setting it to a static address to my router (DL 504).  DEAD.   On windows xp everything works fine, when a Macs hooked up it works fine, 

If you're okay with using a command line prompt, you could bring up a terminal and type ```
ifconfig
``` and see the results.  (This is pretty similar to the Windows command prompt ipconfig.) You should see something similar to this:

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D4:24:84:BA
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1495081 errors:0 dropped:0 overruns:0 frame:0
          TX packets:676228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2106285124 (1.9 GB)  TX bytes:84043348 (80.1 MB)
          Interrupt:20 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18503 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1655823 (1.5 MB)  TX bytes:1655823 (1.5 MB)


```

If you're not inclined to use the command line, there's a GUI program called gnome-nettool that may be of some help

I do think that there is probably a module for the Linux kernel for the ethernet chipset used by your LAN card.  It may be a case of not being compiled into to the kernel used by the live CD.  (Although I doubt it since 8139 is fairly common I think) You could try a different live CD to see if that's the case.

If you're not familiar with the Linux kernel and how it works, then please indulge me for a moment:
The Linux kernel has LOTS of options that can be selected including network cards.  Many of these options are programmed right into the kernel, and others are complied as companion programs that are called modules.  An option that's used all the time is normally compiled directly into the kernel.  Options that are used once and a while are usually compiled as modules.   Normally when  a guy working on a distribution of Linux, he will choose to make all the networking devices modules to the kernel.  These modules will be invoked by the kernel when it discovers the device.  you can see what's currently running as a module for your system by typing the following in a command line terminal:```
lsmod
```Or to see only stuff releated to 8139 type: ```
lsmod|grep 8139
```  When I run this command I get this result:```
lsmod|grep 8139
8139too                26112  0
8139cp                 23680  0
mii                     5632  2 8139too,8139cp

```

That pretty much taps all my knowledge, but there are lots of Really knowledgeable people hanging around in these forums, and they can get you farther down the internet super highway.  Have fun and don't let this speed bump get you down.

---

### Post by xini on 2007-12-11
Thank you soggycornflake.  I will at the earliest chance download a new copy of the Live CD (just to make sure I exclude the problem you mentioned) and start from the beginning again.  I will try all that you have mentioned and if the problem persists I will post the results.

Just as an aside issue, someone has been screaming IPV6 from the rooftops of a forum at me.  Since this sounds like something you get in your arm when you have a bad dose of diarrhea, could I indulge you or someone to explain this to me (and my router) and how I could turn this off.  I was told It was active and I needed to reboot anyway, but thats about all the info i got.....but it's a live CD and the settings would be lost in that event.  I don't think my router can handle this IPV6, there is certainly no mention of this in the manual.

If I can solve this network problem Ubuntu will run like a train for me.

Thanks again.

---

### Post by SoggyCornflake on 2007-12-11
> **xini said:**
> Just as an aside issue, someone has been screaming IPV6 from the rooftops of a forum at me.  Since this sounds like something you get in your arm when you have a bad dose of diarrhea, could I indulge you or someone to explain this to me (and my router) and how I could turn this off.  I was told It was active and I needed to reboot anyway, but thats about all the info i got.....but it's a live CD and the settings would be lost in that event.  I don't think my router can handle this IPV6, there is certainly no mention of this in the manual.

Thanks again.

IPV6 does have some issues, and older hardware may not support it.  I've had to disable it to speed up my internet.   I had found that Firefox took forever to find a site unless I first visited the site with konqueror.  However, I still had network activity.  Check out this [link]("http://ubuntuforums.org/showthread.php?t=87798").  Hopefully that will help.

---

### Post by xini on 2007-12-12
Thanks again soggycornflake.  I read the post and despite following it, still suffer from this problem of having to reboot from the live CD, it appears IPV6 just comes back, well I think it does from what I can see and understand unless i'm doing something wrong.  

I can't commit to a dual  install since my laptop HD is not large enough to cope with this and I dont want to risk my existing data and worst of all a committed Ubuntu install could leave me without network and Internet and help.

I have been told that my equipment here only knows what IPV4 is, so at a guess my problem is likely to because  I have not been able to disable IPV6 in the live CD environment to test that I would have Network and Internet access, then again...thats only a guess.

I may have to abandon Ubuntu for now until i am able to dedicate my laptop to an install rather than a liveCD.

---

### Post by SoggyCornflake on 2007-12-12
Maybe you should try [knoppix]("http://www.knoppix.org/").  I don't know it's using IPV6, but doubt it.  Another one I've used for a recovery system is [DSL ]("http://damnsmalllinux.org/download.html")(Damm Small Linux) It's quite a bit different than Ubuntu, but I like it.  It is definitely not as cutting edge as Ubuntu.  Both of these distros are based on Debian, as is Ubunutu.

---

