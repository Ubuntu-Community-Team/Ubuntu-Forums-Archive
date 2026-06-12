---
title: "No wireless after updating"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by PhibreOptix on 2011-02-07
Hi all I am running Kubuntu 10.10 and it told me that it had several updates to install so I clicked on yes. This included an update to kernel 2.6.35-25-generic after rebooting my machine has no wireless connectivity.

My chipset is bcm4313 and doing lsmod | grep wl shows that the wl module is loaded however I have no wlan0 and network manager doesn't show any wireless connections.

I have tried booting into the old kernel from the GRUB menu but the same problem persists.

---

### Post by jimingkui on 2011-02-07
Maybe your wireless network was blocked,try this : [http://ubuntuguide.net/fix-wifi-failed-issue-after-upgrading-ubuntu-10-10]("http://ubuntuguide.net/fix-wifi-failed-issue-after-upgrading-ubuntu-10-10")

---

### Post by PhibreOptix on 2011-02-08
This command returns nothing. The additional drivers page shows that the STA driver is in use and activated but it's not working.

---

### Post by jenneric on 2011-02-09
I am having similar problems however I have intermittent wireless connectivity. Running Ubuntu 10.10, kernel version 3.6.35-25, BCM4313 chipset.

```
 lshw -C network
``` returns the following: 

  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: 5c:26:0a:13:ca:6d
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 firmware=0.12-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:50 memory:e9600000-e961ffff memory:e9680000-e9680fff ioport:8040(size=32)
  *-network
       description: Wireless interface
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 88:9f:fa:5c:d0:0d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=10.1.25.79 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:e6e00000-e6e03fff

Why is my wireless connection listed as eth1?

---

### Post by wep940 on 2011-02-09
> Why is my wireless connection listed as eth1?
 
Because your built-in ethernet port is eth0.  Remember ethernet and wireless aren't the same.

---

### Post by jenneric on 2011-02-09
Sorry, just wondering why it was not named wlan0 instead. My main problem is the intermittent connectivity. When the wireless stops working I do an ifconfig and there is no longer the eth1. Restart my computer and it is back.

---

### Post by wep940 on 2011-02-09
> **jenneric said:**
> Sorry, just wondering why it was not named wlan0 instead. My main problem is the intermittent connectivity. When the wireless stops working I do an ifconfig and there is no longer the eth1. Restart my computer and it is back.
 
Now I understand what you were asking.  Not sure why it's not wlan0, what does it show in ifconfig and iwconfig when the wireless is working?

---

### Post by TBABill on 2011-02-09
What is the output if you type the following in a terminal ```
sudo rfkill list
```

---

### Post by PhibreOptix on 2011-02-10
I tried that command and it didn't output anything, I ended up just doing a clean install of Kubuntu and not updating to that kernel since it seems to break the wl driver.

---

### Post by jenneric on 2011-02-10
wep940:
when the wireless is working I get the following:
```
ifconfig
```eth0      Link encap:Ethernet  HWaddr 5c:26:0a:13:ca:6d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:e9600000-e9620000 

eth1      Link encap:Ethernet  HWaddr 88:9f:fa:5c:d0:0d  
          inet addr:10.1.25.79  Bcast:10.1.25.255  Mask:255.255.254.0
          inet6 addr: fe80::8a9f:faff:fe5c:d00d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1442 errors:0 dropped:0 overruns:0 frame:135
          TX packets:1206 errors:22 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1077452 (1.0 MB)  TX bytes:290134 (290.1 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
```
iwconfig
```lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:214  Noise level:166
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

---

### Post by TBABill on 2011-02-10
What happens if you ```
sudo apt-get install --reinstall bcmwl-kernel-source
```

---

### Post by TBABill on 2011-02-10
Ok, here's a bit of background that happened to me and I have no idea why it worked. I have the BCM4312, but same driver as your 4313. I just installed Mint 10 KDE and absolutely could NOT get the wl driver to work. I have installed that thing probably 100 times on various distros without issue, but since Mint 10 is based on Maverick we may face a similar issue or just a coincidence...not sure. 
 
Anyway, I could not activate the STA driver (wl), even after running sudo apt-get install --reinstall bcmwl-kernel-source. So I decided to just click b43, which has NEVER worked well for me. And what do you know? It worked. Still working. I have no idea what changed in that kernel version, but b43 works well and the wl wouldn't. I'm sure if I had compiled the wl from source I could get it going, but using the Ubuntu/Mint version would not work.
 
Are you able to give the b43 a shot just as a trial? Just click additional drivers and deactivate the STA and activate b43 to see what happens?

---

### Post by TBABill on 2011-02-10
Disregard. I looked up your chip and it's a newer b/g/n and is not supported by the b43.

---

### Post by wep940 on 2011-02-10
Well, I see eth1 is your wireless - not sure why.  I've never known how that gets changed to wlan0, etc., but perhaps it's a funtion of the driver?
 
Sorry I couldn't help here, but I'm glad you got it working again!

---

### Post by coffeeaddict22 on 2011-02-10
A nice summary of your network status can be got with ```
nm-tool
```; if you keep running into problems it might be worth posting the output of that.

The network naming scheme is a kernel function, and from memory it varies based on the brand of adapter among other things.

After an update it's sometimes worth checking you don't need to reinstall the driver.  It's still on the restricted list so isn't considered kosher; I think that's changing with 11.04, but will depend how quickly Broadcom get the promised open source driver out in a usable fashion (they may have done it already).

---

