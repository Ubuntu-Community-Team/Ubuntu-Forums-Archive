---
title: "D-LINK DWL-G120 USB WIRELESS **HELP!** anyone"
date: 2005-11-26
forum: Networking &amp; Wireless
---

### Post by injectionpa on 2005-11-26
ok I have been working on this for weeks only to find bits and pieces of installation information. I have just installed Ubuntu 5.10 in attempt to get this card to work. I have previously failed with FC4. 

Details.
D-LINK DWL-G120 H/W B1 USB wireless

have installed ?hostap and WLAN-ng with no avail. 

modprobe prism2_usb---good

**lsusb**

Bus 004 Device 009: ID 2001:3701 D-Link Corp. [hex]

**lshw -businfo**

usb@4:6                generic     Generic USB device

** dmesg **

[4371524.473000] usb 4-6: new high speed USB device using ehci_hcd and address 9

there it ends.

**iwconfig **  

nada nothing, no wireless extensions


where can I find the step by step on ensuring the usb hotplug has the device ID directed to a driver... etc.Or a step by step assuming a fresh begining such as do this... do this.. do this.. with none of this then recompile the kernel because I can't find references on how to do this, either. I have used apt-get to install, to this and that file, as the other directions have suggested however then what?? I can't just plug it in and then it works because I it hasn't.... enough rambling.. two + weeks trying to get it to work and nothing yet I know it is very very close. 

any help please... even similar guides for other usb wireless cards could be helpful. I think the system just doesn't know this card hense cannot attach a driver and module to handle the commands.

thanks!! new to linux INJPA

ps I dont want to use ndiswrapper as it isn;'t compat with kismet.

---

### Post by teaker1s on 2005-11-26
install ndisgtk with synaptic it's an easy gui(point and click)
[URL="http://ubuntuforums.org/showthread.php?t=31926&highlight=ndiswapper"]howtohere
[/URL]
 and you need to search wilki or forums for ndiswapper and see how its done if that's no help

---

### Post by injectionpa on 2005-11-26
I'm on it and will try after send. fingers crossed. thanks!

looks like a great tool for ndiswrapper. however I cannot use it in this manner with kismet.

---

### Post by tical2756 on 2007-01-31
I have the same USB wireless card, with Dapper installed 6.06.  It is recognized, but I still cannot connect to the internet.

---

