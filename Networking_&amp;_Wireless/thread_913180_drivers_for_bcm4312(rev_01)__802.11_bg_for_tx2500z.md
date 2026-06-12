---
title: "drivers for bcm4312(rev 01)  802.11 b/g for tx2500z"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by showri on 2008-09-07
08:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

these are my network drivers

my kernel version:

Linux showri-laptop 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux

I do not know where i am going wrong.I get the same results as others but my wireless still shows red and does not work.

WARNING: you should run this program as super-user.
*-network
description: Wireless interface
product: BCM4312 802.11b/g
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:08:00.0
logical name: eth1
version: 01
serial: 00:21:00:4a:b0:77
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11

If anyone has successfully installed the above following drivers for tx 2500z laptop with amd 64 turion x2 ultra please post step by step process as to how to install the drivers.

---

### Post by omidnoorani on 2008-09-22
I have the same wireless card 

Broadcom Corporation **BCM4312** 802.11b/g (rev 01)

On a HP Pavilion **DV6701US** laptop

with **Ubuntu 8.04** - the Hardy Heron - released in April 2008 with the most up-to-date packages and all the updates.



I was able to setup my wireless card to connect to one unsecured network but I can't make it work with networks which have security like WPA or WEP.



It gives up connecting to the network with the following message:

 "**waiting for network key for the wireless network** ..."





Any suggestions?

---

### Post by EvilNemesis on 2008-09-22
I am in the exact same predicament. I have a Dell Latitude D430 using the BCM4312. The card is functioning and I can see all the nearby networks. There just appears to be a problem with encryption (WPA in my case).

Any help is greatly appreciated!

---

### Post by gali98 on 2008-09-22
hmmm... I have the tx2000z, but I think it has the same card. I can connect with no problems...
Have you installed wpasupplicant?
Kory

---

### Post by EvilNemesis on 2008-09-23
No I have not... This is the first time I've heard of it to be honest. I'll give that a shot right now.

---

### Post by shanix on 2008-09-23
Can you run a command:

lspci -vvnn | grep BCM4312

and paste the output?

If I am not mistaken, you will need to install (using an Ethernet cable) the linux-restricted-modules-2.6.24-19-generic [version 2.6.24.13-19.45] on your system for it to work. In short, run an update. =)

Cheers,

---

### Post by EvilNemesis on 2008-09-23
Here is the output:

```
~$ lspci -vnn | grep BCM4312
0c:00.0 Network Controller [0280]: Boradcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
```

---

### Post by EvilNemesis on 2008-09-23
I am running the latest updates as of 9/23. The restricted drivers are also enabled. I just cannot get WPA to work.

---

### Post by EvilNemesis on 2008-09-23
Also, I just checked the Synaptic Package Manager and wpasupplicant is installed.

---

### Post by gali98 on 2008-09-23
hmmmm....
I have the same exact card and it worked just fine on WPA1.
Are you using the generic GNOME network manager? (The one in the taskbar.)
And you are using the restricted driver? (wl)
Kory

---

### Post by shanix on 2008-09-24
Please install pastebinit and show us your syslog.

Command:
$ pastebinit /var/log/syslog

---

### Post by amattheisen on 2010-08-24
I was just experiencing the same problem described in the original post.  The solution for me was to flip the wireless switch on the side of the laptop to enabled.  Maybe this will help others with the same problem.

---

### Post by zdenal on 2010-08-25
Hi all,

The problem is inside the broadcom driver in Lucid.

try this HowTo if it fix your problem.

[http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx](http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx)

---

