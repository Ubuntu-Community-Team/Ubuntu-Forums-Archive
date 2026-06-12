---
title: "bluetooth not detecting nokia e50"
date: 2006-12-11
forum: Networking &amp; Wireless
---

### Post by rkakkar on 2006-12-11
i have a nokia e50 and a soleil bluetooth usb device. i installed gnome-bluetooth and created a link saying gnome-obex-send. however when i refresh the list of devices to send the file to, its unable to detect my phone! :(. i am able to send from my phone to my pc but ubuntu is unable to find my phone! :( any ideas?

---

### Post by dvarsam on 2006-12-11
Hello!

How about trying this out:

[https://wiki.ubuntu.com/D-Link_DBT-122_USB_Bluetooth_Adapter](https://wiki.ubuntu.com/D-Link_DBT-122_USB_Bluetooth_Adapter)

Good Luck!

---

### Post by rkakkar on 2006-12-11
didn't work :(

im pretty much screwed because i don't have windows on my system and i am unable to send anything to my phone! :(

any more help, please?!

---

### Post by rkakkar on 2006-12-13
i even tried connecting the usb cable i got with the phone.. my phone detects the usb connection but ubuntu is oblivious to it! both methods work perfectly fine in windows and atleast dapper used to detect my phone. i guess the bluetooth module in edgy SUCKS!

any help guys?!

---

### Post by rkakkar on 2006-12-15
solved!! :D

i just replaced the gnome-obex-send command to include the address of my phone:

gnome-obex-send --dest=00:18:8D:6C:92:91

and it detected it!.. i'm so glad i'm still sticking with ubuntu

---

### Post by lilmienboy on 2007-01-03
yep, that very last part help me alot, thanks for the tip:mrgreen:

---

