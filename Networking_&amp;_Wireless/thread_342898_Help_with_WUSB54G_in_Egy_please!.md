---
title: "Help with WUSB54G in Egy please!"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by jk610 on 2007-01-20
Hey everyone! Im a brand new Ubuntu user but not new to Linux. But it has been YEARS since Ive worked in a Linux environment and I am way behind the ball. I have a Linksys Wireless-G USB network adapter and I need a little help setting it up. Im not even sure where to start. I read the Sticky at the top for installing in Dapper Drake but I kept getting errors compilng ndiswrapper so I figured id ask here instead of trying that again. 

Here what I can tell you:

lsusb

Bus 004 Device 003: ID 1915:2234
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 413c:2005 Dell Computer Corp.
Bus 001 Device 001: ID 0000:0000

So by the looks of that its not even recognizing my adapter since the only usb devices I have plugged in are my keyboard and the adapter.


iwconfig

eth2           IEEE 802.11b  ESSID:""
                 Mode: Auto  Channel=1  Access Point: Invalid
                 Sensitivity=0/200
                 Link Quality: 0     
                etc... etc... etc...

So if anyone could point me in the right direction of how to get this going it would be much appreciated!

---

### Post by teaker1s on 2007-01-20
unless you post the complete iwconfig output it's hard to say, but from what I can see if you install

[COLOR="Red"]network-manager-gnome[/COLOR]

it appears your wireless is alive

 now on your desktop panel you want to click system administration networking

it's important to make sure that devices show unconfigured so network-manager-gnome can control them. Shutdown and remove ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in passphrase or network key

---

