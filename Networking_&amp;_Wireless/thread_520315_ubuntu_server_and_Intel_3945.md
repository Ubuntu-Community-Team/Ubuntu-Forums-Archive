---
title: "ubuntu server and Intel 3945"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by jsgarvin on 2007-08-08
I just installed Unbuntu Server on my new Dell Vostro 1700 ( I choose 'server' so that it could access > 3GB memory).  I suspect that if I hadn't gone with "Server" this wouldn't be an issue, but memory is memory.

Anyway, I've got ubuntu-desktop and gdm all installed and working great and now trying to get the wireless to work.  

I've installed the linux-restricted-modules-generic as per another thread here somewhere.  I've got the wireless working in the  win****s partition, so I know the interface itself works.

ifconfig and iwconfig both only recognize eth0 and lo.  lspci shows the following...
```
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

If I right click on the netork connection icon on the task bar, the only two options are "Wired Connection" and "Manual Configuration", and if I select "Manual Configuration", the network settings window opens and under connections I only have "Wired Connection" and "Modem Connection"  On another laptop with ubuntu desktop I have "Wireless" options in both of those places.

Anybody have any suggestions?  I imagine there's just some little package or configuration setting that Ubuntu Server doesn't get by default, but I'm not finding any info on what that might be.

---

### Post by noob12 on 2007-08-08
Can you post the results of running these?
```

sudo lshw -C network
ifconfig -a
cat /etc/network/interfaces

```

---

### Post by scxtt on 2007-08-08
> **jsgarvin said:**
> ( I choose 'server' so that it could access > 3GB memory).there's nothing special about the "server" release that would allow you to address > 3GB of memory ... if you have > 3GB of memory, you need to run a 64-bit OS ... if Dell sold you a laptop w/ ~4GB of memory w/o a 64-bit processor, well that's just silly ...

i have a laptop w/ 3945 wireless, and it works in both Ubuntu (feisty) and Fedora (Core 7) ...
```
:> lspci | grep 3945  
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

---

### Post by jsgarvin on 2007-08-08
> **noob12 said:**
> Can you post the results of running these?
```

sudo lshw -C network
ifconfig -a
cat /etc/network/interfaces

```

Certainly...
```
jgarvin@vostro:~$ sudo lshw -C network
Password:
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:f9fff000-f9ffffff irq:17
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:87:37:6e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:f9bfe000-f9bfffff irq:17
jgarvin@vostro:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1C:23:87:37:6E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth0:avah Link encap:Ethernet  HWaddr 00:1C:23:87:37:6E  
          inet addr:169.254.4.250  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21210 (20.7 KiB)  TX bytes:21210 (20.7 KiB)

jgarvin@vostro:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
jgarvin@vostro:~$ 

```

---

### Post by jsgarvin on 2007-08-08
> **scxtt said:**
> there's nothing special about the "server" release that would allow you to address > 3GB of memory ... if you have > 3GB of memory, you need to run a 64-bit OS ... if Dell sold you a laptop w/ ~4GB of memory w/o a 64-bit processor, well that's just silly ...

Well, I swear I saw something somewhere that claimed that the 32bit Server edition was specifically compiled to handle up to (but not more than) 4GB.  Why ubuntu wouldn't just pass the same compile flag to the desktop edition was a mystery to me.  But, now as I google around for that article, all I find are horror stories of people trying to access > 3GB on ANY OS.  So.....

Dell did "offer" up to 4GB for this, but the upgrade was rather expensive compared to just taking the minimum and buying replacement memory from newegg.  So, my plan was to get the computer, make sure Ubuntu Server would instal and that everything basically worked, and then go get the new memory.  Now, I'm rethinking step 2 and may just go up to 2GB (unless I can find a pair of 1.5G modules cheap) and return to the desktop edition.

---

### Post by noob12 on 2007-08-08
OK.  Device is associated with the driver.  No interface.  Not sure why you didn't get an interface for the device.  Let's look at these two for clues:
```

cat /etc/iftab

dmesg

```

Not an excerpt on the dmesg please.  You can attach /var/log/dmesg if that's easier.

---

### Post by jsgarvin on 2007-08-08
> **noob12 said:**
> OK.  Device is associated with the driver.  No interface.  Not sure why you didn't get an interface for the device.  Let's look at these two for clues:
```

cat /etc/iftab

dmesg

```

Not an excerpt on the dmesg please.  You can attach /var/log/dmesg if that's easier.

Thanks for the help noob12, but I went ahead and scrapped the "server" install and went back to desktop... for now (it's having it's own display issues, which I'll start a new thread for).  If I change my mind again and come back to server, and I still have the same issue, then I'll re-energize this thread. Thanks again.

---

### Post by noob12 on 2007-08-08
And it worked for you then?

---

### Post by jsgarvin on 2007-08-08
> **noob12 said:**
> And it worked for you then?

Once I got past the display issues, first reboot gave me some kind of "Hal" error, but on the next reboot, that just went away by itself and wireless connected flawlessly.  Downloading 111 updated packages over a WPA encrypted connection right now.

---

### Post by scxtt on 2007-08-09
> **jsgarvin said:**
> Dell did "offer" up to 4GB for this, but the upgrade was rather expensive compared to just taking the minimum and buying replacement memory from newegg.  So, my plan was to get the computer, make sure Ubuntu Server would instal and that everything basically worked, and then go get the new memory.  Now, I'm rethinking step 2 and may just go up to 2GB (unless I can find a pair of 1.5G modules cheap) and return to the desktop edition.2 points i think you should keep in mind:

1. if your laptop DOES NOT have a 64-bit processor, don't waste your $ on getting 4gb of memory for it - you WILL NOT be able to use it all ...
2. to my knowledge there are no 1.5Gb RAM modules ... if you want 3Gb total, you could have:
[indent]2 1Gb modules
2 512Mb modules[/indent]

that is, if you have 4 slots (not sure all laptops do, mine only has 2) ... it's also very likely this is DDR2 memory and it's in your best interest to make sure things are paired up (i.e. matching 1Gb, matching 512Mb) ...

if you want to use X, DON'T install the server version, it'll have no benefits for you ...

---

