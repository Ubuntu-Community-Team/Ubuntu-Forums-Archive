---
title: "Trouble with Broadcom BCM4318"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by beagler on 2008-08-25
Hi everyone. I'm very new to linux as well as ubuntu, and I wasn't sure if this should go in the beginners forum or if this is the right place. anyways, I think I have a Broadcom BCM 4318 wireless card and i cannot get it to work. Everything I've read says that Ubuntu 8.04 should support these cards natively, but nothing I do will let me access the internet without using a wire. My questions are:

1) how can i tell if my computer is loading the driver and if its working properly?

2) if the driver is working properly, what else do i need to do to get my internet running wirelessly?

Ive already gone into my network settings and made some changes. I've tried a few things, but currently i have the wireless connection checked and i've unchecked roaming mode. In the properties menu I typed in the network name which multiple windows machines are using to connect. I wasn't sure about password type since there's currently no password set, so i left it on WPA personal with the password field blank. I switched connection settings to a static ip address and entered in all the info that ipconfig gave me from a windows box. 

On my ubuntu machine, here is some output from commands in the console:

lspci:
...
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
...

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:e0:b8:b5:e5:01  
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:feb5:e501/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:525 errors:0 dropped:0 overruns:0 frame:0
          TX packets:441 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:474322 (463.2 KB)  TX bytes:71124 (69.4 KB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:82000 (80.0 KB)  TX bytes:82000 (80.0 KB)

What am I doing wrong? As I said, I am very new to this, and my lack of knowledge in linux has been very discouraging in my attempt to switch over from windows. I would really like to never use windows again, but I cannot seem to get anything done on my linux install. Thanks in advance for any help.

---

### Post by caljohnsmith on 2008-08-25
Welcome to the forums, beagler. :)
> **beagler said:**
> 
1) how can i tell if my computer is loading the driver and if its working properly?
Using the "lsmod" command will list all your loaded modules (drivers). Since I assume you are not using ndiswrapper at this point, please post the output of:
```
lsmod | grep 43
```
> **beagler said:**
> 
2) if the driver is working properly, what else do i need to do to get my internet running wirelessly?

I'll bet the issue is with your driver at this point. Take a look at [Ayuthia's comprehensive broadcom guide]("http://ubuntuforums.org/showthread.php?t=779754") for getting your BCM4318 working. If you need help with that guide, let me know.

---

### Post by beagler on 2008-08-26
Thanks a lot for your help. So I came home from work today with more work to do, and I didnt want to do it at all. In my procrastination I checked the forums and found your post, so I got excited to give this thing another go now that someone had offered thier assistance. I grabbed my laptop, rebooted it since I had accidentally left it on, and then when I booted it up again the driver manager popped up with a little checkbox asking me if I wanted to enable the driver for my wireless card. Last night after numerous re-boots the only thing that showed up in there was a driver for a graphics card.

Basically, I checked the box, rebooted, unplugged the wire, and then came on to these forums and posted this message without being plugged in at all! 

So maybe something I did in my three hours of fiddling last night helped it recognize that it could just go and find the driver so easily. I don't know what happened, but I like it. 

I'm stoked to mess around more in linux and now I can procrastinate my work a little bit more and try to learn A good text editor in linux. Thanks so much for your help which I fourtunately turned out not to need. 

Grateful as a child on christmas,

-Andy

---

### Post by caljohnsmith on 2008-08-26
That's great news, Andy; glad your wireless is working now. If you have any more issues or questions about Ubuntu, don't hesitate to pop in the forums again. :)

---

