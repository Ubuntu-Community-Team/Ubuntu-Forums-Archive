---
title: "Intel e100 lan not working"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by chrisbedford on 2008-06-16
Hey... please be patient with me, I have been as patient as I know how but have now come to the end of my rope! Two major issues that I am now fighting with and frustration is no doubt affecting my ability to find answers, but be that as it may I am up against a brick wall here.

I downloaded & installed the Live CD installation of Ubuntu 8.04. I don't know if there are any other versions... that's the one I found & used.

FIRST ISSUE:
After installation the screen was at the correct native resolution for my screen, 1280 x 1024. System - Administration - Hardware drivers only lists one item: nvidia_new, enabled, status is red dot "not in use". No proprietary drivers are in use on this system. Nothing can be changed on this screen.

Now after the first reboot it comes up at 800x600, and there are no higher res options to select. Huh? Also all the stuff that was on the desktop first time around is missing - in fact there's nothing at all on the desktop.

SECOND ISSUE:
No network connection, and this is what has me tearing my hair out. I have searched, and find nothing but "wireless" help. The problem is no network connectivity *at all*. It would seem the wired ethernet should "just work", but in this case... well, let's go through the suggested list of steps:-

1. How were you trying to get connected? 
motherboard integrated NIC

2. What hardware are you using? 
intel D845GEBV2 m'brd

3. Who is your Internet Service Provider
N/A, can't even get a LAN ping

4. Which version of Ubuntu are you using?
Ubuntu 8.04

5. Can you get online with any other method? e.g. if you have a wifi problem, can you connect with ethernet?
Well, uh, no

6. How are you getting online to post on this forum?
I'm priveleged to have a second computer running... another OS

7. Include the output from the following commands

lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:05.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:05.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:05.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 82)


lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000


lshw -C network
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 82
       serial: 00:0c:f1:e8:f7:7c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s


8. Do you dual-boot with Windows?
No!!!

9. Other information that I can think of, to try to head off further questions:

- cable connected, lights flashing

- in System - Administration - Network, I have tried "Roaming" (what does that mean? help is no help...), dhcp, and static all to no avail

- adding DNS servers when static address is set doesn't seem to "stick"? (i.e. I come back to the screen and DNS box is empty again)

- the Wired Connection item icon is a blue cable with an RJ45-style plug in front of a suitable socket - not a PC interface card as illustrated in the documentation for Sys - Adm - Netw. Is this relevant, or just a minor change in ver 8 that hasn't yet found its way into the docs?

- System - Admin - Network Tools shows three interfaces: loopback, eth0, and eth0:avahi. LB shows expected 127.0.0.1 address, eth0 shows only IP v6 info, and eth0:avahi shows a private range IP address (169.254.10.239) which indicates to me no connectivity at all...?

- I found a post under Networking that suggested there might be a workaround: Chili555 said to do this:
sudo su
ok that results in root@ instead of {username}@

# rmmod forcedeth
ERROR: module forcedeth does not exist in /proc/modules
...I didn't go on, didn't think it would be a good idea after that

# modprobe forcedeth msi=0 msix=0
# /etc/init.d/networking restart

So what now? Please? Thanks!
Chris

---

### Post by ugm6hr on 2008-06-17
One thread per issue please - so we'll stick to ethernet for now.

Reboot with LAN plugged into router and give output from following:
```
ifconfig
route -n
```

I think that ethernet card is supported.  The lshw output shows that the driver (e100) is installed OK.

Could it possibly be a hardware issue?  The flashing lights seem to indicate that the router and LAN card are communicating.  But being unable to ping is inconsistent with that.

How is the router set up?  DHCP or static?

---

### Post by chili555 on 2008-06-17
> Chili555 said to do this:That was for an nVidia nForce ethernet card, not an Intel PRO/100 VE. While it won't do any harm to try to insert the wrong module, it also won't do any good. Please be careful about issuing commands if they don't match your situation.

I do appreciate your confidence, though. It looks to me like ugm6hr has your situation well in hand. Ugm6hr might also like to see:```
dmesg | grep e100
```

---

### Post by chrisbedford on 2008-06-17
OK thanks - found enough information here:

[http://ubuntuforums.org/showthread.php?t=766879&highlight=screen+resolution](http://ubuntuforums.org/showthread.php?t=766879&highlight=screen+resolution)

to hack the video thing after a bit of head-scratching. So moving on...

"Could it possibly be a hardware issue? The flashing lights seem to indicate that the router and LAN card are communicating" - well one would hope not. The machine was working fine under windoze before I reinstalled with Ubuntu... 

But going with the principle that once all the usual suspects have been eliminated, whatever remains, however unlikely - etc etc, thank you, it looks like one port on my DAMN router is duff. Switched to a different port, I now have a valid IP address from the DHCP server and am downloading new plugins for Firefox.

No matter how many times coincidences happen, I never suspect the next time that I've been hit by another one.

Thanks again, strength to your arm!

---

### Post by chrisbedford on 2008-06-17
> That was for an nVidia nForce ethernet card, not an Intel PRO/100 VE. While it won't do any harm to try to insert the wrong module, it also won't do any good. Please be careful about issuing commands if they don't match your situation.

Hmmm... :-)

> I do appreciate your confidence, though.

Heh... for "confidence" read "gung-ho"? Too many years in tech support, I guess... I was assuming the "forceth" was referring in some way to "force the ethernet card to..."{whatever} - now I realise (after your comment above) that it refers to the GeForce chipset. Yeah, like I said, too may years in techsupp - too little patience - too much frustration!

---

### Post by chili555 on 2008-06-17
We usually don't give Jedi trainees the light saber on day one, but the command to force the ethernet card to do amazing things is *ethtool.* You can learn more with the command:```
man ethtool
```Amazingly, there are *man*, or manual pages for about every command in Linux.

---

### Post by chrisbedford on 2008-06-17
> **chili555 said:**
> Amazingly, there are *man*, or manual pages for about every command in Linux.

Yes! Very useful when you know what command you want to use! But getting to that point is trickier! ;-)

---

