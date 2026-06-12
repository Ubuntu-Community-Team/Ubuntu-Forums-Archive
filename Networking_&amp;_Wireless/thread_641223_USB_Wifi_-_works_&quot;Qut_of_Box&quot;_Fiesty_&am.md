---
title: "USB Wifi - works &quot;Qut of Box&quot; Fiesty &amp; Gusty!!!"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by nunnst on 2007-12-15
If you are looking to buy a Wifi adapter and want it to work "out of box", the "[COLOR="Blue"]Ativa Wireless G USB Adapter[/COLOR]" worked perfectly for me.  It's available at Office Depot (Ativa is a store brand of Office Depot - its actually made by Belkin) for less than $40.  I successfully use it on both Feisty and on Gutsy, Have it running on two different laptops, 1) HP dv8XXX w/ AMD Turion-64, 2) an OLD Compaq Armada E500 (Pentium III - 500 Mhz).  

Be sure to disable Ipv6 on Gutsy (thanks to this forum I was already prepared to do that).  I have not tested the range (prolly not so great for a $40 adapter) or any security other than WEP.  

The following is from lshw command.

      $ lshw 
              *-usb
                   description: Generic USB device
                   product: USB2.0 WLAN
                   vendor: Belkin
                   physical id: 1
                   bus info: usb@1:1
                   version: 48.10
                   capabilities: usb-2.00
                   configuration: driver=zd1211rw maxpower=500mA speed=12.0MB/s

No ndiswrapper, broadcom, or Madwifi nightmares to mess with!

Good luck!

---

