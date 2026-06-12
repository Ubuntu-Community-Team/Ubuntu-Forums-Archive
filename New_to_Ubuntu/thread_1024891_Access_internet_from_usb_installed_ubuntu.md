---
title: "Access internet from usb installed ubuntu"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by dave1 on 2008-12-29
Hi

I have installed ubuntu 7.04 on a usb hdd so that I can use ubuntu on my works laptop.  I log in to windows xp and then log into ubuntu on my usb hdd.  Ubuntu then works fine except that I have 2 problems.  The biggest being that I cannot access the internet.  The secondary problem is that I would like to be able to import files from my c:/ drive (windows xp).

Can anyone help me?

---

### Post by BDNiner on 2008-12-29
how did u install ubuntu on the laptop? you would need to enable read and write support for ntfs follow this post.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

I need more information about the network card and the kind of laptop. post the output of 
```

lshw -C network

```

---

### Post by dave1 on 2008-12-29
I get the following:

*-network
description: Ethernet interface
product: RTL-8029(AS)
vendor: Realtek Semiconductor Co., Ltd.
physical id: 3
bus info: pci@00:03.0
logical name: eth0
version: 00
serial: 52:54:00:12:34:56
width: 32 bits
closk: 33MHz
capabilities: ethernet physical
configuration: broadcast=yes driver=ne2k-pci driver version=1.03 latency=o multicast=yes
resources: ioport:c100-clff irq:11

hope that's the info that you needed

---

### Post by dave1 on 2008-12-29
Re: Access internet from usb installed ubuntu 

--------------------------------------------------------------------------------

I get the following:

*-network
description: Ethernet interface
product: RTL-8029(AS)
vendor: Realtek Semiconductor Co., Ltd.
physical id: 3
bus info: pci@00:03.0
logical name: eth0
version: 00
serial: 52:54:00:12:34:56
width: 32 bits
closk: 33MHz
capabilities: ethernet physical
configuration: broadcast=yes driver=ne2k-pci driver version=1.03 latency=o multicast=yes
resources: ioport:c100-clff irq:11

hope that's the info that you needed

---

### Post by ieee488 on 2008-12-29
Ubuntu is only detecting a wired Ethernet card - no wireless.

---

### Post by BDNiner on 2008-12-29
ok so it is detecting the network card. Did u run this command while the network cable is plugged in? can you also post the outputs of 
```

ifconfig

```

you don't need iwconfig since u don't have a wireless card.

---

### Post by dave1 on 2008-12-29
Yes I ran it with the ethernet cable plugged in.

ifconfig results in the following:

eth0
Link encap:Ethernet  HWaddr 52:54:00:12:34:56
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:17 errors:0 dropped:0 overruns:0 frame:0
TX packets:68 errors:0 dropped: 0 oeverruns:0 carrier:0 collisions:0 txqueuelen:1000
RX bytes:3128 (3.0 KiB)  TX bytes:9528 ((.£ KiB)
Interrupt:11 Base address:0xc100

lo
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:225.0.0.0
inet6 addr:  ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:14 errors:0 dropped:0 overruns:0 frame:0
TX packets:14 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0
RX bytes:758 (758.0b)  TX bytes:758  (758.0 b)

iwconfig results in:

no wireless extensions.

no wireless extensions.

---

### Post by BDNiner on 2008-12-29
you are not getting an ip address. iwconfig will not do anything unless you have a wireless card installed. I am guess you are trying to use a wired connection. try 
```

ifconfig eth0 down

```
then
```

ifconfig eth0 up

```

---

### Post by dave1 on 2008-12-29
Hi 

Sorry for the delay.  When I typed in ifconfig eth0 down my laptop froze.

For both ifconfig eth0 down and ifconfig eth0 up I get:

SIOCSIFFLAGS: Permission denied

---

### Post by BDNiner on 2008-12-29
i am sorry put sudo before the commands
```

sudo ifconfig eth0 down

```

---

### Post by dave1 on 2008-12-29
When i put sudo in front, I am getting no response at all.  I've shut down and re-logged in to double check and I still get no response, it's as if ~I have simply hit the return key without typing a command.

---

### Post by BDNiner on 2008-12-29
This is strange, does the network work in windows?

---

### Post by dave1 on 2008-12-29
Yes it does.  When I am in Windows, I can use both the built in wireless and the cable.

---

### Post by ShadowfoxXXX on 2008-12-29
use wubi and install ubuntu on the same drive as windows. That'll solve everthing

---

### Post by dave1 on 2008-12-29
I was hoping not to do that because I do not want to be installing anything on the c:/ drive because this is my work laptop.  When I descovered that ubuntu could be installed on a usb hdd I thought that this was a good option that would give be the best of both worlds.

---

### Post by BDNiner on 2008-12-29
this is strange, I always thought that RealTek's cards worked out of the box with linux. what kind of wireless card does your computer have? And what kind of laptop is it?

---

### Post by dave1 on 2008-12-29
The laptop is a hp Compaq nx6310.

Sorry but I may now be about to give you duff info because I am not very technical.  I went into the Modems icon in the Control Panel on windows which told me that I have an Agere Systems HDA Modem #2.  Is that the wireless card or should I be looking for something else?

---

### Post by dave1 on 2008-12-29
Think I've just found the correct info:

Intel(R) PRO/Wireless 3945ABG Net

---

### Post by BDNiner on 2008-12-29
no that is the modem. the wireless card can be found under network connections in the control panel.

---

### Post by dave1 on 2008-12-29
I think my 2nd reply crossed with your last one.  does Intel(R) PRO/Wireless 3945ABG Net sound correct.  I found that in the properties tab of the wireless connection in the network connections icon.

---

### Post by BDNiner on 2008-12-29
yeah lol. your card should work out ot the box although there are some issues with this card dropping connections. but it should be detected by default.

---

### Post by dave1 on 2008-12-29
By the sounds of it what I need to do is try using my usb hdd on another machine and seeing if I can then detect a modem through ubuntu. That way I will at least know if the problem is with the laptop that I am currently using or not.  Thanks for all your time.  I will let you know in a couple of days when I have had chance to try a different machine.

---

