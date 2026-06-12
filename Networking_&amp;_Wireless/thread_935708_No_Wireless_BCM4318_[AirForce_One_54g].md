---
title: "No Wireless: BCM4318 [AirForce One 54g]"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by m.sky on 2008-10-01
I cannot seem to connect to a wireless network in general, but really having problems with WAP / WAP2 networks.  

Anyone have any ideas?

>   *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:03:25:33:3e:12
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.65 latency=0 module=sky2 multicast=yes
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:03:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:43:1b:07
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

> 00:00.0 Host bridge [0600]: ATI Technologies Inc Radeon Xpress 200 (RS480/RS482/RX480/RX482) Chipset - Host bridge [1002:5951] (rev 01)
00:02.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI-X Root Port [1002:5a34]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 11)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376]
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 02)
00:14.6 Modem [0703]: ATI Technologies Inc SB400 AC'97 Modem Controller [1002:4378] (rev 02)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M24 1P [Radeon Mobility X600] [1002:3150]
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller [11ab:4351] (rev 10)
03:05.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410] (rev 01)
03:07.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
03:0e.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. IEEE 1394 Host Controller [1106:3044] (rev 80)

> x86_64

> [   40.010493] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  196.819763] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  217.021952] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by superprash2003 on 2008-10-02
hope this helps [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by m.sky on 2008-10-08
Thank you, I have not tried that yet and I will ASAP!  I hope it works because to be cable-required in a wireless world just sucks. :)

---

### Post by snakep on 2008-10-09
I have tried the fix for Hardy in the WifiDocs article you linked, but I have problems removing and reloading ndiswrapper.  The first time I tried it, it seemed to work, though my card still didn't work because I didn't have the firmware, apparently.  Now, however, the machine totally locks up when I enter the sequence:

```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

```

Using "rmmod" instead of "modprobe -r" has the same effect.

Does anybody know what could be causing it to lock?  I have to force the machine to power off, then reboot.  Is it possible to still find a log of what happened?

Thanks,

Jeremiah

---

### Post by m.sky on 2008-10-11
I cannot get it work either ... I am having some type of 'module=ssb' error. I followed the directions to fix that but it did not seem to fix it.

Any additional advice on getting WiFi to work?

```
msky@Ubu-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:03:25:33:3e:12
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=xxx.xxx.x.xx latency=0 module=sky2 multicast=yes
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:03:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:43:1b:07
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

:confused:

---

### Post by kevdog on 2008-10-11
What driver are you trying to use?  Did you download the appropriate one from the wiki from the link above?

---

### Post by stormcrow_wolf on 2008-10-11
This is the same problem I'm having with my laptop (see new broadcom woes).  It seems to be somewhere between the initial 8.04 release kernel and the most recent kernel update some patch somewhere broke something in the b43 module.  The only way I've been able to fix it is to keep the initial kernel and not update it at all.  (Yes I know it's a security issue, but not having wireless working is not an acceptable trade off in this case).  NDISwrapper doesn't work either since you must remove the ssb module as well, which deactivates the b44 module since ssb is a dependency for b44 (which is the wired ethernet) which means no networking at all.  By the way, NDISwrapper generally isn't advisable on a system running the x86_64 version of ubuntu.  (32 bit driver on a 64 bit kernel... yeah.. bad idea).

---

### Post by kevdog on 2008-10-11
Im not sure if that is true!!!

---

### Post by m.sky on 2008-10-15
Technically none of the drivers on the website are for the 4318 ... if I recall correctly there is the 4316 and some others, but none for the 4318.

I downloaded what I thought is the correct drivers(4318 and Linux).  Is there a terminal code I can use and post to show which driver I am using?  I apologize but I am somewhat new to Ubuntu.  I am good at following directions but have not had enough exposure with Ubu yet to think freely.

Any additional information would be vastly helpful as I really like wifi and would like to get it working.  :popcorn:

---

### Post by m.sky on 2008-10-16
At this point I was wondering if anyone has a step-by-step on how to completely remove my WiFi drivers, and NDIS wrapper so I can start this process completely fresh.  Lets start at square one.

I really do appreciate any information that is provided.  :)

---

### Post by Ayuthia on 2008-10-16
> **m.sky said:**
> Technically none of the drivers on the website are for the 4318 ... if I recall correctly there is the 4316 and some others, but none for the 4318.

I downloaded what I thought is the correct drivers(4318 and Linux).  Is there a terminal code I can use and post to show which driver I am using?  I apologize but I am somewhat new to Ubuntu.  I am good at following directions but have not had enough exposure with Ubu yet to think freely.

Any additional information would be vastly helpful as I really like wifi and would like to get it working.  :popcorn:

The no-fluff link does have step 2a as the driver option for the 4318 rev 02 card.  You could try using that.  However before going through that step, it looks like you have not been able to load ndiswrapper yet because ssb is in use.  Can you do me a favor and post the following results from the Terminal:
```
ndiswrapper -v
ndiswrapper -l
lsmod|grep -e b43 -e b44 -e ssb -e ndiswrapper -e wl -e bcm43xx

```The first command will check the version of ndiswrapper that you are using.  The second command will check and see if the windows driver is loaded properly.  It should show device present if it is working ok.  The last command is going to see what wireless modules you have currently running.

Once we are able to see this, we will try to load ndiswrapper to see if we can get it to work.

---

### Post by m.sky on 2008-10-17
Thank you for the response but I actually got it working via a different post.

I ended up using the Synaptic Package Manager (System > Administration > Synaptic Package Manager) then located the BCM43xx-fwcutter, installed it and "BAM" (to quote Emeril) it worked.

If you want to check it out, here is the link:
[HTML]http://ubuntuforums.org/showthread.php?t=424994[/HTML]

---

