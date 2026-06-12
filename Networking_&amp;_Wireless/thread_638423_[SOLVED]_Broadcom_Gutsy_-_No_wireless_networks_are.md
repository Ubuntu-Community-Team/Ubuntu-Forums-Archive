---
title: "[SOLVED] Broadcom Gutsy - No wireless networks are listed anymore"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by Coward on 2007-12-12
I had Broadcom working under Feisty, and for over a week on Gutsy. I don't know why, but now no wireless networks are listed (they are definitely still there). I cannot connect to the network by choosing "Connect to other Wireless Network."

I don't know much about linux, but I've gone through setting this card up before. Here are all the facts I know, most of them are probably useless but this will save time-

I'm using ndiswrapper. It says bcmwl5 hardware present: yes in Windows Wireless Drivers. I got this far using the thread called Broadcom the easy way. This is what it displayed when wireless was working.

Typing in lspci | grep Broadcom returns the following output:
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

The text "blacklist bcm43xx" is in /etc/modprobe.d/blacklist

The contents of /etc/iftab says it has been moved to /etc/udev/rules.d/70-persistent-net.rules. This file is now
```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.


# PCI device 0x10de:0x0269 (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:1b:24:7c:a1:76", NAME="eth0"

# PCI device 0x14e4:0x4311 (ndiswrapper)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:1a:73:7f:63:5a", ATTRS{type}=="1", NAME="wlan0"

# PCI device 0x14e4:0x4311 (bcm43xx)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:00:1a:73:7f", NAME="eth1"

```

fn+f2 may or may not turn off the wireless. I never tried when it was working. I'm just mentioning that I know this so you don't ask me about it.

I tried using the firmware under the restricted drivers. It also didn't work so right now it is unchecked (not in use). This is how it was while wireless worked.

Does anyone have any ideas for me to try? Thanks in advance just for reading all of that.

---

### Post by kevdog on 2007-12-12
Can you post:


lshw -C network
iwlist scan

---

### Post by Coward on 2007-12-12
Here it is. By the way, I think you were the person who helped me last time this wasn't working.

```

jake@jake-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:7f:63:5a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
jake@jake-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

```

---

### Post by Dynaflow on 2007-12-12
I have that same card in my cheapo Compaq laptop I almost got into a fistfight over at Fry's on Black Friday.  There is an in-depth installation/troubleshooting guide [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy?highlight=%28bcm43xx%29").  I followed the instructions for Feisty [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28bcm43xx%29") for my fresh install of Gutsy, and it's been working well so far.

---

### Post by Coward on 2007-12-12
I've tried and failed to use the native driver before, so I'm going to wait and see if kevdog (or someone else in the next 24 hours) has something to add before I try it again. If I do try it though, I'll use that guide. Which step 2 did you take (A, B, C, or D) in that guide? Or did you compile ndiswrapper from source?

edit: just compiled ndiswrapper from source. Nothing is different.

---

### Post by Coward on 2007-12-13
*bump*

So I've been searching the internet to see what may be the problem. I'm not sure what the file /etc/network/interfaces is supposed to look like but this doesn't seem right:

```

auto lo
iface lo inet loopback


#iface eth0 inet dhcp






































auto eth0




```

It makes no mention of wlan0, the wireless network. I'm not an expert, but shouldn't there be something in there?

---

### Post by Coward on 2007-12-14
Well I think the /etc/network/interfaces file is the problem, so can someone with wireless working please post their file?

I also found this while experimenting. It seems I need to do something to configure wlan0 (probably will be fixed by editing /etc/network/interfaces?).
```

jake@jake-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

jake@jake-laptop:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
jake@jake-laptop:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
jake@jake-laptop:~$ 

```

Edit: Done some research. I don't think /etc/network/interfaces is the problem anymore. Not sure what is.

More information:
```

jake@jake-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by sherrife on 2007-12-14
Hi mate,

I have the exact same problem, using ndiswrapper as well.  I have edited /networking/interfaces and added the subnet mask and the static ip of the router.... still no luck.

I'm waiting eagerly for a solution as well!

---

### Post by Coward on 2007-12-19
I've fixed it on my computer!

What I did was this, there might be some unnecessary steps here but o well. Here's the site: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff).

Anyway, first I followed step 2a. Then I followed the steps to compile ndiswrapper from source. After that I went to Synaptic package manager and downloaded nisdiswrapper-common and ndiswrapper-utils-1.9

Finally I realized that the physical switch on my computer for the wireless card was off. This may have been my problem the whole time. Thanks for everyone's help. I feel stupid, yet happy.

---

