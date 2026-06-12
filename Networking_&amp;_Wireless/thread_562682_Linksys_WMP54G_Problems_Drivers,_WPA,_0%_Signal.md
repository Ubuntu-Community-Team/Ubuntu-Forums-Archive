---
title: "Linksys WMP54G Problems: Drivers, WPA, 0% Signal"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by MrAjax on 2007-09-29
I've been running Feisty since right after it was released, and I got my wireless card working fine, but I recently got my room mate to switch from XP, and I'm trying to get his Linksys WMP54G working with WPA, since my wireless only works with WPA.  I know it has the rt61 chipset, and I have tried things from many other threads.  My first instinct was to use WICD, since that worked great on my system.  When we tried that it got stuck when obtaining an IP address and wouldn't connect.  I also noticed that all the available AP's had 0% signal.  I've tried drivers, wpa_supplicant confiuration, basically anything I could find available. I've seen many plausible solutions in other threads, but they don't work or they are not quite the problem I'm having. I'd like some specific help instead of just a link to another thread (unless you're absolutely sure it will help).

Here's the output from lshw -C network and modinfo rt61:

lshw -C network
*-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 2
       bus info: pci@05:02.0
       logical name: ra1
       version: 00
       serial: ##:##:##:##:##:##
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT61STA driverversion=1.1.0 CVS latency=64 multicast=yes wireless=RT61 Wireless
       resources: iomemory:fe2e8000-fe2effff irq:20

modinfo rt61
filename:       /lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt61/rt61.ko
license:        GPL
description:    Ralink RT61 802.11abg WLAN Driver 1.1.0 CVS CVS
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     180F8980D3385B365E8F654
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.20-15-generic SMP mod_unload 586 
parm:           debug:Enable level: accepted values: 1 to switch debug on, 0 to switch debug off. (int)
parm:           ifname:Network device name (default ra%d) (charp)

---

### Post by Dark-Angel on 2007-09-29
If you find an answer to this porblem could u let me know as I am having the excat some problem. I have the same card and i can see it but 0 signal and won't connect. I have tried seaching drivers but can't find anything. 
Thanks

---

### Post by unisol on 2007-09-29
i have  an rt61 card and had to do thisin a terminal:

ifconfig ra1 up
iwconfig ra1 mode managed
iwconfig ra1 essid "my network"
iwconfig ra1 channel your channel
iwpriv ra1 set NetworkType=Infra
iwpriv ra1 set AuthMode=WPAPSK
iwpriv ra1 set EncrypType=TKIP
iwpriv ra1 set WPAPSK="mykey"
iwpriv ra1 set SSID="my network"
dhclient ra1 

i hope this helps.

---

### Post by noob12 on 2007-09-29
No personal experience, but some have suggested rutilt : [http://cbbk.free.fr/bonrom/](http://cbbk.free.fr/bonrom/)  along with recent builds of the drivers from serialmonkey's sources (which it looks like you have).

I think the most recent versions of the drivers are supposed to work better with the 2.6.22 kernel that will come with Gutsy, so I hope a bunch of ralink users will start to have a better experience.

ADDED: in a nice coincidence there's now this new thread with a HOWTO on that:  [http://ubuntuforums.org/showthread.php?t=554089](http://ubuntuforums.org/showthread.php?t=554089)

---

### Post by MrAjax on 2007-09-29
> **unisol said:**
> i have  an rt61 card and had to do thisin a terminal:

ifconfig ra1 up
iwconfig ra1 mode managed
iwconfig ra1 essid "my network"
iwconfig ra1 channel your channel
iwpriv ra1 set NetworkType=Infra
iwpriv ra1 set AuthMode=WPAPSK
iwpriv ra1 set EncrypType=TKIP
iwpriv ra1 set WPAPSK="mykey"
iwpriv ra1 set SSID="my network"
dhclient ra1 

i hope this helps.


It worked! Thank you so much, you have single-handedly regained me some linux cred from my room mate.

For anyone else reading this:
the command dhclient ra1 made the signal for the AP go from 0 to 78% and connected to the network, simply amazing.

I put all the commands above into a bash script and set it to run at login.

---

### Post by Dark-Angel on 2007-09-29
i tried doing that also but when i put in the ifconfig ra1 up
i got dhclient ra1SIOCSIFFLAGS: Permission denied

---

### Post by unisol on 2007-09-30
did you put sudo in front of the commands?

---

### Post by Dark-Angel on 2007-10-01
Thanks. I put sudo and it was working however it still hasn't got wireless working for me.
This is a screenshot of what I was getting. Not sure if you can help from it.
My wireless is still just at 0% signal and won't connect.
[IMG]http://i16.photobucket.com/albums/b21/cam_m/sc.jpg[/IMG]

---

### Post by sulligogs on 2007-10-01
Hiya

I am recent to Ubuntu and would like to draw your attention to step 5 of my HOWTO at [http://ubuntuforums.org/showthread.php?t=554089](http://ubuntuforums.org/showthread.php?t=554089)

Before using RutilT I was getting random crashes.  The authors' of this software obviously know what they're doing because that has now been completely eliminated and I have a network that I can successfully utilise.

Give it a try.  The worst that can happen is no signal, I suppose.  By the way, with step 5 - try an IP like 192.168.0.X or something.  Something that works with your network's subnet.  Implementing pure DHCP in the etc/interfaces/network file gave me strange results with RutilT.  Just let RutilT take care of DHCP from the HOWTO.

Thanks for your time.

---

### Post by unisol on 2007-10-01
Dark_Angel, have you tried wicd 1.3.3? it might be what yiu need? it has to be this version as it has support for the rt61. it can be found at: [http://wicd.sourceforge.net/phpbb/](http://wicd.sourceforge.net/phpbb/)

---

