---
title: "Connecting to the wireless"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by teaicky on 2010-11-30
Hey everyone, 

I just downloaded Ubuntu on my HPmini, so I'm really new to it... I got a problem connecting to the wireless. I have searched bunch of guides and materials online, but still haven't solved the problem. 

I found this post [http://ubuntuforums.org/showthread.php?t=1349254](http://ubuntuforums.org/showthread.php?t=1349254) in the forum, but I couldn't open the .iso link he provided (it has been removed...). Also, I couldn't install apt-get install wicd since I'm not connected to the internet. I just didn't figure out a way how to connect the wireless. 

Anyway, here is what I got when I clicked on the network connection. 

Wired Network
disconnected
VPN Connections >
                 
Also, here is what I got entering the code "iwconfig"

lo                no wireless extensions.
eth0            no wireless extensions.

Thanks a lot...!

---

### Post by mr_luksom on 2010-11-30
Does ubuntu recognize your wireless card?

```
lshw -c network
```

---

### Post by teaicky on 2010-12-01
But I am not using a wireless card...
Anyway here is what I got. 

 [FONT=&#23435;&#20307;]  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 60:eb:69:6e:4a:a6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:42 ioport:5000(size=256) memory:50010000-50010fff memory:50000000-5000ffff memory:50020000-5002ffff
  *-network UNCLAIMED
       description: Network controller
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:56000000-56003fff
[/FONT]

---

### Post by teaicky on 2010-12-01
Sorry I mean, I think my wireless card has not been set up... The above is what I got.

---

### Post by andymorton on 2010-12-01
Have you installed any wireless drivers. Depending on your connection you won't be able to connect without them. If not go to Administration > Additional Drivers and install the B43 one. 

andy

---

### Post by anewguy on 2010-12-01
The easiest way to get your wireless working (BCM4313) is:

- temporarily hardwire a connection to your router
- in a terminal window:

sudo apt-get update

- go to System/Administration/Additional Drivers - if there is a driver there for your wireless, enable it and wait a few minutes as it may need to download something via the hardwire connection

- physically disconnect the hardwire cable

- right-click network manager - be sure "Enable Wireless" shows and is enabled

- left-click network manager - do wireless networks show now?

Things to remember:

- there are other ways of getting this working if you cannot temporarily hardware a connection

- if this is the first time this adapter has been used to connect to your router, and if your router has MAC filtering enabled, you need to add the MAC of the adapter to the router table

Dave ;)

---

### Post by teaicky on 2010-12-01
I don't find anything in the Additional Drivers now. I will try to connect to a cable tonight. 

Thanks a lot everyone!!

:)

---

### Post by Trandre on 2010-12-01
I just solved a simular problem just now by.  

1.system--> administration --> users and groups --> Advanced settings --> user priveliges --> enable contect to wifi and ethernet

2. turn off the wifi hardware switch(this was a laptop) restart your computer --> turn on wifi hardware switch and presto I was on.

---

### Post by teaicky on 2010-12-01
> **Trandre said:**
> I just solved a simular problem just now by.  

1.system--> administration --> users and groups --> Advanced settings --> user priveliges --> enable contect to wifi and ethernet

2. turn off the wifi hardware switch(this was a laptop) restart your computer --> turn on wifi hardware switch and presto I was on.

I just tried but it didn't work... I think I miss a wireless driver. I will try connecting to a cable tonight. Thanks a lot! 

:)

---

### Post by teaicky on 2010-12-02
> **anewguy said:**
> The easiest way to get your wireless working (BCM4313) is:

- temporarily hardwire a connection to your router
- in a terminal window:

sudo apt-get update

- go to System/Administration/Additional Drivers - if there is a driver there for your wireless, enable it and wait a few minutes as it may need to download something via the hardwire connection

- physically disconnect the hardwire cable

- right-click network manager - be sure "Enable Wireless" shows and is enabled

- left-click network manager - do wireless networks show now?

Things to remember:

- there are other ways of getting this working if you cannot temporarily hardware a connection

- if this is the first time this adapter has been used to connect to your router, and if your router has MAC filtering enabled, you need to add the MAC of the adapter to the router table

Dave ;)

This works perfect. I got connected to the wireless now!! 

Thanks a lot for your help! :p

---

### Post by anewguy on 2010-12-02
Glad it's working for you!

Do us a favor and using "Thread Tools" on this thread, mark the thread as "Solved" so that others with a similar problem can look here and see if it helps them or not.

Dave ;)

---

