---
title: "VMware/ itunes"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by evilbuntu on 2008-08-21
i have recently installed vmware on my 8.04 server for toying around with. i decided that maybe since all my media was installed on an external HD to this same system i could also install itunes to access the media and use itunes all in one tower. the problem i am having is trying to get vmware to see the external hardrive.

has anyone gotten this to work. i have tried to install the usb's then go to vm>usb but nothing appears. 

can you use an external usb HD with vmware or is this an imaginary task?

thanks

also i have tried two suggestion in this forum.

one was adding a new physical drive which i couldnt get to work (and was afraid of losing the data on)

and the other was removing the  "#" in some tags in oen of the system files.

---

### Post by c2olen on 2008-08-21
I have VMware server 1.0.6 running on a Debian 4.1 server. I have no problem what so ever attaching USB disks to a VM. Even a USB1.1 device :-)

I have some questions for you;

[LIST=1]
[*]What type of VMware are you running? Workstation, Player, Server ?
[*]Can you access the USB disk in your Ubuntu installation?
[/LIST]
If number 2 answers to no, than you will most probably get an issue connecting the not-working usbdisk to a VM. If 2 is yes, the way to do it, depend on th VMWare product.

---

