---
title: "USB modem won't connect to internet after reboot"
date: 2005-06-15
forum: Networking &amp; Wireless
---

### Post by silent-red on 2005-06-15
I was choosing an option in the speedtouchconf.sh that it will connect automatically after a reboot, but everytime I reboot the internet connection wont work. I have to run undo.sh and reboot and run again speedtouchconf.sh. I don't know where the trouble is. Can anyone have an idea on this.

Thanks

---

### Post by desdinova on 2005-06-15
Change the lines in /etc/speedtouch.conf as this

LOAD_USBCORE=0
LOAD_USBINTERFACE=0
LOAD_NHDLC=1

---

### Post by silent-red on 2005-06-16
Thanks,.. usb modem is now running smoothly,

Anyway, what are these options?
[quote=desdinova]
LOAD_USBCORE=0
LOAD_USBINTERFACE=0
LOAD_NHDLC=1
[/quote]

---

