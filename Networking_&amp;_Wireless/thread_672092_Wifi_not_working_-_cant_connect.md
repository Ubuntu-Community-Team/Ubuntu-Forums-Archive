---
title: "Wifi not working - cant connect"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by ZagaN1904 on 2008-01-19
Hello

Please bare in mind that I'm a linux newbie, only tried it for 3-4 days now.

I've read that the intel 4965 would work "out-of-the-box". It wasn't working for me, so I started out by reading and trying a whole bunch of things, manually installing drivers, trying out windows drivers through ndiswrapper, etc. Nothing worked, it actually got worse, after a while I couldn't even see the available wifi networks, and next my laptop wouldn't boot (capslock blinking, something about kernel panic). So I reinstalled ubuntu, upgraded everything and now I'm able to view the wireless networks, how good the connection is and so fourth. The problem is that I can't connect, I don't know what I'm doing wrong.. 

lspci gives me a bunch of info, the network related are:

04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
0e:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)

dmesg | grep 4965 gave me:

[   17.849650] Allocate Port Service[0000:00:1c.0:pcie02]
[   15.352000] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.1.0
[   15.352000] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   15.356000] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   15.728000] iwl4965: Tunable channels: 13 802.11bg, 19 802.11a channels
[   15.728000] wmaster0: Selected rate control algorithm 'iwl-4965-rs'

Any other commands I need to run to give you guys info to help me?

So it seems like the system recognizes everything, the driver seems to be installed. Once I got to the point that the wifi connected, and told me how good the connection was (about 50-60%), but firefox etc. wouldn't work anyhow..

Btw. I'm running Ubuntu Gutsy 2.6.22-14-generic, it seems like 4965 isn't working very good with this build? [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/)

Please help, as I'm using this laptop for school, I need a working wireless.

---

### Post by ZagaN1904 on 2008-01-20
No help? :(

I've looked a bit at the bug page, but can't quite make out what to do?

---

### Post by Hightide on 2008-01-20
HI

have a look at Kevdog's tutorial, you may find it useful

[http://ubuntuforums.org/showthread.php?t=596797](http://ubuntuforums.org/showthread.php?t=596797)

:)

---

