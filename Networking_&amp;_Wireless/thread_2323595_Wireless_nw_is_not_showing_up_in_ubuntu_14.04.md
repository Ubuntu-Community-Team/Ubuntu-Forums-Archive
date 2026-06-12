---
title: "Wireless n/w is not showing up in ubuntu 14.04"
date: 2016-05-06
forum: Networking &amp; Wireless
---

### Post by abhishek29 on 2016-05-06
[COLOR=#111111][FONT=Ubuntu]Wireless n/w is not showing up in ubuntu 14.04 after formating my pc, However I am able to connect internet via LAN. Please find below link contains wireless-info.txt file information[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][http://paste.ubuntu.com/16198709/](http://paste.ubuntu.com/16198709/)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]sudo iwconfig[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]display below results[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]eth0 no wireless extensions.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]lo no wireless extensions.

for more info please find below url : 

[http://postimg.org/image/3w8obuych/](http://postimg.org/image/3w8obuych/)

Thanks 
[/FONT][/COLOR]

---

### Post by Bucky Ball on 2016-05-06
Welcome. I'm taking a wild guess and saying you have a wireless dongle plugged in to a USB hub? I can't see it in either output.

Have you accidentally trodden on the dongle lately or is this an internal wireless card? ;)

---

### Post by abhishek29 on 2016-05-07
Hi,
thanks for prompt response , I m using internal wireless card , my wireless connection working fine earlier with ubuntu 12.04 but this problem occur when I upgrade my ubuntu with 14.04.

---

### Post by Bucky Ball on 2016-05-07
In that case, the 'lsusb' command (shown in your second link) is of no use here as that shows inserted USB devices. Please omit in future posts. 

Well, I'm stumped as I see nothing in your wirelessinfo output, but try this just to confirm:

> sudo lshw -C network

... and post back the output between code tags (see the green link in my signature). 

Can you plug in an ethernet cable so you are online, do an update/upgrade, reboot with the cable out and then run the command I've given again, please?

---

