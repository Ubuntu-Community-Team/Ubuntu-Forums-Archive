---
title: "Dell 1210/5700 Verizon card &amp; USBSERIAL???"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by jimbojones on 2007-03-01
Hello all.  I just installed 6.10 and updated it.  I am trying to follow this tutorial  [http://www.krontab.com/](http://www.krontab.com/)  I have the same laptop and Dell Wireless 5700 PCI Express Mini Card (CDMA EVDO).  

i do lsusb and see my vendor and product id.  Its after this that i get lost.

I do this command
$ sudo usbserial vendor=0×413c product=0×8114

and I get back sud: usbserial: command not found

I am completly lost (new to linux)  and can not find out how to get the card set up as a ttyUSB device   Any help is greatly appreciated.
:)

---

### Post by jimbojones on 2007-03-01
Well I ran an update, but USBSERIAL stil comes back as command unkown.  Is there something I need to install first possbily?

---

### Post by jimbojones on 2007-03-01
uh, i think i might have found, i will post back shorty.

---

### Post by maxseamus on 2007-03-28
jimbojones, were you able to get this working? I am getting the same message.

Thanks,

---

