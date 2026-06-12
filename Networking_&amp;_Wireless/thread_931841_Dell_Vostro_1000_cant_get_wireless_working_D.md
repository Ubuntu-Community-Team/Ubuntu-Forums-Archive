---
title: "Dell Vostro 1000 cant get wireless working D:"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by nuroxs on 2008-09-27
I tried following some guides to get my wireless working.

First I tried using this guide. [Here]("http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html")

All I basically did was copy and paste anything that the person said to do in the terminal. It ended up not working.

Then I tried to follow this guide since the previous one didn't work. Here[http://ubuntuforums.org/showthread.php?t=297092]("http://ubuntuforums.org/showthread.php?t=297092")

I copied and pasted each line into the terminal. It didn't work.

Then I reread the first part of that guide and it said that if you had tried to install ndiswrapper before the guide will most likely not work and that it recommends reformatting. I would gladly reformate but I don't have the ubuntu cd (a friend let me borrow his) and I no longer have the CD. However, the guide recommends an alternative method but it doesn't go into detail about how to do the alternative method to clean previous attempts.

I found a new guide with that should work for my computer since the guide was made for my computer. And it is very simple. I already tried to follow the guide but it didnt work. [Here]("http://www.roxburgh.net/projects/dell-vostro-1000-vista-linux-dual-boot")


So my question is how do I clean my previous attempts at trying to get my wireless working so I can just start refresh and use the third guide to get my wireless working.

Thanks for the help.

My wireless card is a Dell Wireless 1395 802.11g Wi-Fi Internal Card

[http://pastebin.com/f6dffcf0b](http://pastebin.com/f6dffcf0b)

lspci

---

### Post by nuroxs on 2008-09-27
bump

---

### Post by sam_delta on 2008-09-27
<sam_delta> nuro, do you see this message?, im in a separate window
<Nuro> yeah
<sam_delta> nuro, do you see this message?, im in a separate window
<sam_delta> opps ok
<sam_delta>  nuro , does, "iwconfig" now returns something other than "no wireless extensions"
<Nuro> it says no wireless extensions
<Nuro> on lo and eth0
<sam_delta> on all interfaces
<sam_delta> what about wlan0
<Nuro> i dont see that
<sam_delta> run "sudo ndiswrapper -m"
<Nuro> module configuration already contains alias directive
<Nuro> is what it says
<sam_delta> umm
<sam_delta> use this command "lshw -C network"
<sam_delta> and check under network , if it says "unclaimed"
<Nuro> WARNING: you should run this program as super-user.
<Nuro>   *-network UNCLAIMED     
<Nuro>        description: Network controller
<Nuro>        product: BCM4312 802.11b/g
<Nuro>        vendor: Broadcom Corporation
<Nuro>        physical id: 0
<Nuro>        bus info: pci@0000:05:00.0
<Nuro>        version: 01
<sam_delta> if it doesnt say unclaimed, look for "driver ="
<Nuro>        width: 64 bits
<Nuro>        clock: 33MHz
<Nuro>        capabilities: cap_list
<Nuro>        configuration: latency=0
<Nuro>   *-network
<Nuro>        description: Ethernet interface
<Nuro>        product: BCM4401-B0 100Base-TX
<Nuro>        vendor: Broadcom Corporation
<Nuro>        physical id: 0
<Nuro>        bus info: pci@0000:08:00.0
<Nuro>        logical name: eth0
<Nuro>        version: 02
<Nuro>        serial: 00:21:70:78:b5:1e
<Nuro>        width: 32 bits
<Nuro>        clock: 33MHz
<Nuro>        capabilities: bus_master cap_list ethernet physical
<Nuro>        configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.2.2 latency=64 module=ssb multicast=yes
<Nuro> thats what it says 
<Nuro> up there
<sam_delta> alright, it says unclaimed , that means no driver is claiming the device,
<Nuro> driver=b44 ?
<sam_delta> thats the wired ethernet
<Nuro> ok
<sam_delta> the upper one is the wirless, looks unclaimed
<sam_delta> ima copy u some commands to see if it claims it, gime a sec
<Nuro> k
<sam_delta> sudo rmmod b43
<sam_delta> sudo rmmod b43legacy
<sam_delta> sudo rmmod wl
<sam_delta> sudo rmmod ssb
<sam_delta> sudo rsudo rmmod ndiswrapper
<sam_delta> wong one the last
<sam_delta> should be "sudo rmmod ndiswrapper"
<sam_delta> sudo modprobe ndiswrapper
<sam_delta> sudo modprobe ssb
<Nuro> when i type rmmod b43legacy it says ERROR: Module b43legacy does not exist in /proc/modules
<sam_delta> alright, no problem
<sam_delta> proceed
<sam_delta> we trying to remove it anyways, so no problem it does not exixt
<sam_delta> exist*
<sam_delta> now, check if its still unclaimed
<sam_delta> lshw -C network
<Nuro> k
<Nuro> gimme a sec
<sam_delta> k
<Nuro> im still doing them
<sam_delta> k
<Nuro> WARNING: you should run this program as super-user.
<Nuro>   *-network               
<Nuro>        description: Wireless interface
<Nuro>        product: BCM4312 802.11b/g
<Nuro>        vendor: Broadcom Corporation
<Nuro>        physical id: 0
<Nuro>        bus info: pci@0000:05:00.0
<Nuro>        logical name: wlan0
<Nuro>        version: 01
<Nuro>        serial: 00:22:5f:16:1b:87
<Nuro>        width: 64 bits
<Nuro>        clock: 33MHz
<Nuro>        capabilities: bus_master cap_list ethernet physical wireless
<Nuro>        configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,09/20/2007, 4.170. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
<Nuro>   *-network
<Nuro>        description: Ethernet interface
<Nuro>        product: BCM4401-B0 100Base-TX
<sam_delta> great, now its claimed by ndiswrapper
<Nuro>        vendor: Broadcom Corporation
<Nuro>        physical id: 0
<Nuro>        bus info: pci@0000:08:00.0
<Nuro>        logical name: eth0
<Nuro>        version: 02
<Nuro>        serial: 00:21:70:78:b5:1e
<Nuro>        width: 32 bits
<Nuro>        clock: 33MHz
<Nuro>        capabilities: bus_master cap_list ethernet physical
<Nuro>        configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.2.2 latency=64 module=ssb multicast=yes
<sam_delta> great, now its claimed by ndiswrapper
<Nuro> ok
<Nuro> so what should i do
<sam_delta> now "iwconfig" should return you something else than no wireless interface
<sam_delta> confim me that
<Nuro> lo        no wireless extensions.
<Nuro> eth0      no wireless extensions.
<Nuro> wlan0     IEEE 802.11g  ESSID:off/any  
<Nuro>           Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
<Nuro>           Bit Rate:54 Mb/s   Tx-Power:32 dBm   
<Nuro>           RTS thr:2347 B   Fragment thr:2346 B   
<Nuro>           Power Management:off
<Nuro>           Link Quality:0  Signal level:0  Noise level:0
<Nuro>           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
<Nuro>           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
<sam_delta> alright, now, try to connect to a network, (click on the upper right corner, on the network icon, and click on a wireless network)
<Nuro> ok
<Nuro> one sec
<sam_delta> kk

---

### Post by nuroxs on 2008-09-27
Part 2 - this runs those commands via a boot file so we dont have to run them every time. I hope this chat helps others with my same problem. I'll definitely use it as my reference.

(11:39:27 PM) Nur1: yeah
(11:40:03 PM) Nur1: my terminals open
(11:40:04 PM) sam_delta: type in the terminal "sudo gedit /etc/rc.local"   a text file will open, tell me when it opens
(11:40:25 PM) Nur1: ok
(11:40:26 PM) Nur1: i opened it
(11:40:31 PM) Nur1: what do i save in it?
(11:40:55 PM) sam_delta: ok, now, you need to type in there the following commands, (type them Just before the "exit 0"
(11:41:01 PM) Nur1: k
(11:41:11 PM) sam_delta: rmmod b43
(11:41:20 PM) sam_delta: rmmod b43legacy
(11:41:26 PM) sam_delta: rmmod wl
(11:41:36 PM) sam_delta: rmmod ssb
(11:41:49 PM) sam_delta: rmmod ndiswrapper
(11:41:58 PM) sam_delta: modprobe ndiswrapper
(11:42:05 PM) sam_delta: modprobe ssb
(11:42:16 PM) Nur1: ok
(11:42:19 PM) Nur1: its all been added
(11:42:23 PM) Nur1: save and quit?
(11:42:30 PM) sam_delta: in that same order, note that they do not have the "sudo"
(11:42:34 PM) sam_delta: yeah, save and quit
(11:42:45 PM) Nur1: ok
(11:42:57 PM) Nur1: so that just runs those commands every time is start my pc?
(11:42:58 PM) sam_delta: what we just did, is add those commands to the "boot" script, so you do not have to type them everytime you boot
(11:43:04 PM) sam_delta: yeah, exaclty

---

