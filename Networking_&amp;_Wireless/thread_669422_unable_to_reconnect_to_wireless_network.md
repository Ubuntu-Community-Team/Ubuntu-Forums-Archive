---
title: "unable to reconnect to wireless network"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by stefan47 on 2008-01-16
ok heres my problem.. in order to connect to my wireless network i boot up then i must switch on the wireless hardware button and enter the folowing commands
   "sudo modprobe ndiswrapper"
    "sudo dhclient wlan0"
this then connects me but if i then manually disconnect (using the button) i am unable to reconnect again without rebooting my computer.  Is there an way to reconnect without having to  reboot. I am sorry if this is not very clear but i am a newbie and so any help would be much appreciated.. cheers

---

### Post by luisromangz on 2008-01-16
Well, firstly, you don't have to type those commands manually every time you boot your computer, you can just add them (without sudo) to the /etc/rc.local file. Its contents are launched on boot.

And about using dhclient... why you don't just use NeworkManager?

About the button issue, maybe you haven't blacklisted another driver that may conflict with nediswrapper, to do this add a line in /etc/modprobe.d/blacklist.

---

### Post by stefan47 on 2008-01-16
cheers 4 answering. if i include lines in /etc/rc.local file   i cant connect because i have 2 manually turn on wireless (using button) first. if i dont i have 2 reboot 2 connect. in windows this button automatically comes on but i dont know how 2 do this in ubuntu. is there anyway to do this. cheers once again

---

