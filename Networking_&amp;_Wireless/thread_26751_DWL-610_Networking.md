---
title: "DWL-610 Networking"
date: 2005-04-13
forum: Networking &amp; Wireless
---

### Post by chambs10 on 2005-04-13
Back to Linux after a few years.  I loaded 5.04 on my ze4600 laptop last night. Everything seems to work great, except for my DWL-610 wirless card.

My DWL-610 wirless card shows up in the Device Manager under the cardbus controller as a DWL-510. Also, in the Network Settings I only see my modem and eth0 (internal ethernet) devices.

Where do I start from here?  I have been so far out of the loop that I'm not aware of the ndiswrapper.  Theoretically it makes sense, but I'm hesitant to try it if the system already recognizes the card.

Just in case someone needs the config under /etc/networking/interfaces this is what I have even when the card is inserted:

-------------------------------------------------
#the loopback network interface
auto lo
iface lo inet loopback

#This is a list of the hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
              script grep
              map eth0

# The primary network interface
iface eth0 inet dhcp
------------------------------------------------

Thank you for your help.

---

### Post by haaglin on 2005-04-14
Use the ndiswrapper to load your windows drivers. I couldn't find the guide, it looks like it moved, But you can try searching google for it. I think you find ndiswrapper in synaptic. and if i remember correctly, you should do something like this after installing ndiswrapper: 

ndiswrapper -i dwl610.inf (where dwl610.inf is the name of the win driver)

sudo modprobe ndiswrapper

And i think you may have to copy the *.inf file to your computer, don't work if you run it from the cd. 

Anyone correct me if i'm wrong.

---

### Post by PlaidAvenger on 2006-02-05
I'm also having difficulty getting my DWL-610 working.  Mine is also being detected by Ubunto as a DWL-510.  I've tried following the instructions in a few of the other threads on this topic but haven't had any luck.

When I type in the 'sudo modprobe ndiswrapper' command I get the following:

> FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

I'm running Ubunto 5.10 on an IBM Thinkpad 600e.

It's been a LONG time since I've used Linux, so I'm a little lost here, and I appreciate any help.

Thanks in advance.  :-)

Plaid

---

