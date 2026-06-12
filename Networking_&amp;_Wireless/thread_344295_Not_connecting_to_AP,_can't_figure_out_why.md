---
title: "Not connecting to AP, can't figure out why?"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by seventynine on 2007-01-22
Can't get Ubuntu to connect via wifi. However, internet via ethernet cable is working just fine. Man.........I've been reading the forums since 11AM but can't get wireless to work.

I have an x86 with Belkin F5D7000 (Broadcom 4306 chipset). My wifi access point is a Linksys WRT54g with essid "hokiepokie" unprotected (for now) on channel 11.

This is what Ive done to the system so far:
-Installed Ubuntu 6.10 Edgy.
-Installed all the updates.
-Installed Network Manager.

When I open the Network Manager, it shows the "Connect to other wireless networks". I select it, and then enter the Network Name as "hokiepokie" and Wireless Security "None". It searches for about a minute and then returns to "connected " via "Wired Connection". Btw, I can't see the wireless networks around me. So I instead have to enter the essid name by keyboard.

I pulled some commands, if they help:
> asha@ashapc:~$ iwlist
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event


> asha@ashapc:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


> asha@ashapc:~$ lshw

[........*removed the redundant other hw info*..........]

q:5
        *-network:1 DISABLED
             description: Wireless interface
             product: BCM4306 802.11b/g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: d
             bus info: pci@00:0d.0
             logical name: eth1
             version: 03
             serial: 00:11:50:1b:e0:2c
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master ethernet physical wireless
             configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE 802.11b/g
             resources: iomemory:cefea000-cefebfff irq:11
asha@ashapc:~$ 

??DISABLED??

Btw, this is my second installation. The first time I tried fwcutter and after I did "modprobe" and restart, even my wired connection stopped working altogether (some error about a missing glade file). I dont know what happened??

My level in linux is very new. Though I have been using windows for nearly 7 yrs. Hoping to make the jump if wifi can work. Any help is appreciated very much!

---

### Post by seventynine on 2007-01-23
Nevermind fixed it. The problem was that the PCI based WLAN card needs to have the firmware loaded each time the hardware starts. This particular PCI card doesnt have flash memory to store the firmware, just RAM, and hence requires Ubuntu to "load" the card with the firmware like loading ram. 

So to set it up, I extracted the correct firmware via fwcutter. Then I programmed a script to send firmware to the pci WLAN card everytime the computer boots. And voila, it works.

I'm surprised this pci card does not have the flash memory to store firmware. I guess thats how the manufacturers make these cards so cheap these days.

---

