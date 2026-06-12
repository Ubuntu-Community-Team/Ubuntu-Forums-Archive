---
title: "New to Linux - No Wireless"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by 7ate9 on 2008-09-24
I installed Ubuntu Hardy Heron using Wubi on Vista a few days ago. I must say it works really well having completed the available updates. I do have one major problem - no wireless [I'm using an Acer Aspire 5100 laptop].

I checked other posts and tried installing Wicd. It works fine for my wired connection but it's still not picking up my wireless network.

I checked other posts and saw something about ndiswrapper so I installed that from the "Synaptic Package Manager". I also installed the Windows Wireless Drivers thing from "Add/Remove...". Unfortunately, I have to find the drivers myself and I don't know where to find these. Help.

I typed the following in the "Terminal" and this is what i got:

-laptop:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: [REMOVED]
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=[REMOVED] latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

and also:

-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



What do I need to do to get my wireless to work?

---

### Post by Bakon Jarser on 2008-09-24
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

---

### Post by willca on 2008-09-25
You can try the one in the repository and see if it does make a difference rather than going the ndiswrapper route right away (which so far for me has worked 100% of the time as long as you got the windows drivers).

sudo apt-get install b43-fwcutter
follow the prompts..

You might need to reboot after this.

To check if its working..

sudo iwlist wlan0 scan

---

### Post by 7ate9 on 2008-09-25
> **willca said:**
> You can try the one in the repository and see if it does make a difference rather than going the ndiswrapper route right away (which so far for me has worked 100% of the time as long as you got the windows drivers).

sudo apt-get install b43-fwcutter
follow the prompts..

You might need to reboot after this.

To check if its working..

sudo iwlist wlan0 scan
When i tried 

*sudo apt-get install b43-fwcutter*

I got
[I]
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/I]

I already have the ndiswrapper though so where could i find some windows wireless drivers?

Also, i tried what was posted here:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

and I saw a new driver called "wl" in *System>Administration>Hardware Drivers*. This is actually enabled and in use but still no wireless. Could it be something with Wicd Manager?

---

### Post by willca on 2008-09-25
Looks like some other process is running that has put a lock on the repository cache locally.

If you still want to go with this since I dont know for sure if that windows driver will actually work for ya unless you probably download it from your computer manufacturer site.

ps -ef | grep adept
And kill -9 that process.

Then proceed with installing the b43-fwcutter module.

---

### Post by 7ate9 on 2008-09-25
Ok here's what I got:

[I]sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.[/I]


Then:

[I]-laptop:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down[/I]

The network isn't down. I connected a few mins ago on Vista on the same laptop.

---

