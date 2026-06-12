---
title: "Loaded Ubuntu No Wireless Connection"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by rtrahan on 2008-12-18
Here is the information about my wireless adapter:
Atheros Comm/AR242X/802.11abg/Wireless PCI Express Adapter/PCI ID: 14e4:1693.
Any help would be greatly appreciated. My second day on Ubuntu so step by step directions would be appreciated.

---

### Post by jboy012000 on 2008-12-18
Hi,

Which version of Ubuntu have you installed?, if it is the latest version 8.10lts then Ubuntu should pick up any wireless network in range, all you have to do is select your network, put in your wep key and your connected.

Cheers

---

### Post by pshootr on 2008-12-18
Hi. check this out, hope it helps.

[http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)

---

### Post by Peter09 on 2008-12-18
Can you post the output of the terminal commands

```
lshw -C network
```

and

```
ifconfig
```

---

### Post by carml on 2008-12-18
If you installed Ubuntu 8.04,to get your Atheros Wireless Lan work,you can install ndiswrapper from System->Administration->Synaptic package manager.You need also a Windows driver like this one Wireless_Atheros_V5.3.0.67_XP_XB63_XB62(WHQL),and you have to go to System->Administration->Hardware driver and disable both:Hardware access layer(HAL) and Support for Atheros....Once you've done you have to load the driver with ndiswrapper. :p

---

### Post by rtrahan on 2008-12-18
I loaded 8.04 and thanks for the link but I don't know enough about the commands yet to do it, that's why I need step by step, and I'll only need it once I'm a fast learner;

Here's the output:
description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:48:3a:67
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5787m-v3.22 latency=0 module=tg3 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
rtrahan@Home-PC:~$ 

Here is the ifconfig:rtrahan@Home-PC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:48:3a:67  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth0:avahi Link encap:Ethernet  HWaddr 00:1e:ec:48:3a:67  
          inet addr:169.254.5.186  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1138 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57088 (55.7 KB)  TX bytes:57088 (55.7 KB)

---

### Post by andreasis on 2008-12-18
Hi!

You're in luck.  I have hardy installed on my acer aspire one, and it has the same wireless driver as yours.

Here are easy and clear instructions that I used to get me up and running:

[https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Hardy%20Heron%20(8.04.1)%20on%20the%20Acer%20Aspire%20One](https://help.ubuntu.com/community/AspireOne#Install%20Ubuntu%20Hardy%20Heron%20(8.04.1)%20on%20the%20Acer%20Aspire%20One)

Scroll down the equivalent of 2 pages until you reach the network section.

---

### Post by rtrahan on 2008-12-18
I don't know what I am doing wrong. I downloaded three files:madwifi-ng-r1531-20060427.tar.bz2 is suppose to be unpacked. I loaded that file into my documents. I typed /home/rtrahan/Documents/tar xjf madwifi-ng-r1531.20060427.tar.bz2 per the instructions but I get a "no such file or directory.

---

### Post by ByteJuggler on 2008-12-18
> **rtrahan said:**
> I don't know what I am doing wrong. I downloaded three files:madwifi-ng-r1531-20060427.tar.bz2 is suppose to be unpacked. I loaded that file into my documents. I typed /home/rtrahan/Documents/tar xjf madwifi-ng-r1531.20060427.tar.bz2 per the instructions but I get a "no such file or directory.

The "tar" command is not in "/home/rtrahan/Documents/" so you should not prefix/specify that as its location.  Rather, you want to specify that path as the location of the "madwifi" file, e.g.

```
tar xjf /home/rtrahan/Documents/madwifi-ng-r1531.20060427.tar.bz2
```

You can shorten that to:
```
tar xjf ~/Documents/madwifi-ng-r1531.20060427.tar.bz2
```


More complete/usefully, you can instead do:

```
cd ~/Documents
ls -al
tar xjf madwifi-ng-r1531.20060427.tar.bz2
ls -al
```

The first command changes the current folder to your Documents folder.  The second lists the contents in long format.  You should see the madwifi file there.  The third extracts the file from the current folder (as no path is specified.)  The fourth relists the contents, and should show the extracted folder.

You can also extract the archive from the GUI by navigating there and double clicking the file, and then extracting it using the archive manager.

---

### Post by andreasis on 2008-12-18
Not that I disagree with the way to go about it,, but,, considering it being rtrahan's second day with linux,, why get into the technicalities of tar already when you can just do it graphically at first,, just double-click and extract anywhere,, it's all gui. ^_^

---

### Post by rtrahan on 2008-12-18
Thank you so much, I got it extracted from the GUI..I'm almost there so could you walk me through  the next steps. I been working at this for three days and this is the closes I have ever come. The next direction was to type cd to the madwifi which I did successfully, then it said to type "make", but I am getting an error that says 'uudecode' tool not found on your system...the exact string is
 ~Documents/madwifi-ng-r1531-20060427 make

Thanks in advance

---

