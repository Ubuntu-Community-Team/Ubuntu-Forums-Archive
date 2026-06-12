---
title: "[SOLVED] Wireless 4965AGN on Dell M1710 not working"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by MickSulley on 2008-05-23
Hi,
I have a Dell XPS M1710 with a 4965AGN wireless card.  It was working on Gutsy but then I did a fresh install of Hardy to clean up the machine.  Now I have no wireless connection.  I have installed Wicd as that helped a lot under Gutsy, but there is no wireless connection showing at all.  I have read many other posts and tried lots of fixes but I am getting nowhere.  Can anyone help please?

Thanks
Mick

---

### Post by mapes12 on 2008-05-23
Hi Mick

We will need some info from you to make progress. Please could you post the output from:

```
sudo lshw -C network

cat /etc/resolv.conf

ifconfig

iwconfig

iwlist scan

cat /etc/network/interfaces

```

---

### Post by MickSulley on 2008-05-23
Hi,
Thanks for helping, here is the info - 

mick@mick-laptop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:dc:e7:14
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5752-v3.19 ip=192.168.0.3 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
mick@mick-laptop:~$ 

mick@mick-laptop:~$ cat /etc/resolv.conf
search Belkin
nameserver 192.168.0.1


mick@mick-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:8b:dc:e7:14  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:fedc:e714/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97446 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92770 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:114937741 (109.6 MB)  TX bytes:10527859 (10.0 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1814 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1814 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:90700 (88.5 KB)  TX bytes:90700 (88.5 KB)

mick@mick-laptop:~$ 
mick@mick-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

mick@mick-laptop:~$ 
mick@mick-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

mick@mick-laptop:~$ 
mick@mick-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp
wireless-key "128 bit WEP code here"
wireless-essid Sulley


iface eth0 inet dhcp


mick@mick-laptop:~$

---

### Post by MickSulley on 2008-06-02
Can anyone give me any pointers on this please?

---

### Post by stchman on 2008-06-02
> **MickSulley said:**
> Hi,
I have a Dell XPS M1710 with a 4965AGN wireless card.  It was working on Gutsy but then I did a fresh install of Hardy to clean up the machine.  Now I have no wireless connection.  I have installed Wicd as that helped a lot under Gutsy, but there is no wireless connection showing at all.  I have read many other posts and tried lots of fixes but I am getting nowhere.  Can anyone help please?

Thanks
Mick

My Toshiba has a 4965AGN and it works OOB with Hardy.  I use network-manager and it is great.

Here is a common problem.  Did you inadvertantly turn the wireless switch off?  This happens.

---

### Post by MickSulley on 2008-06-02
Yes I have checked that.  I believe that teh line that says it is UNCLAIMED means that the driver is not installed, but I don't have a clue where to go from there
Any ideas?

---

### Post by tvphil on 2008-06-02
I also have the same intel 4965 card using Ubuntu Hardy 64 bit version and mine works. Hardy is more picky about network settings, as once I lost them after a recent upgrade in the Linux kernel, but I did get them back. First of all, I need more info. about your current config. If you go to system>administration>network, are you set for "roaming enabled"? If not, do it, then when it asks for your network key (assuming you are encrypted and not running in the clear), enter the key. Hopefully, your network will be found. I believe the driver for this card is in the kernel, so it should be installed. That's why I think it sounds like a configuration issue, not a driver issue.Just for the record, my computer is also a Dell, it's an inspiron 1520.

---

### Post by MickSulley on 2008-06-06
I assume by 'Roaming enabled' you mean the tick box next to wireless network, in which case yes that is on, but I still do not see any wireless network.  I have tested the network on a windows laptop, it does work.

Any other ideas?

---

