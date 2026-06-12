---
title: "usbnet connection between laptop and desktop"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by ushaba on 2007-02-11
i am trying to connect my desktop running edgy to my laptop running vector linux, namely because i only have one internet connection and want to be able to take files from one computer to the other easily. later, if i can set this up, i will hopefully also be able to enable both computers to browse on the same internet connection, but let's worry about the first issue first. the laptop seems to have no problem recognizing usb0 as a network interface, but for some reason i can't figure out where ubuntu expects the usb connection to be. i added the lines  ```
auto usb0 
iface usb0 inet dhcp
allow-hotplug usb0

```
to my /etc/network/interfaces config file, but sadly, this appears to do nothing. what am i doing wrong exactly? i just want ubuntu to realize that something is connected to it.
cheers/thanks

---

### Post by ushaba on 2007-02-13
some may notice that most of the forums on this site about usbnet have no replies. does anyone know how to connect two computers (one on ubuntu and one on some other os) together via usb link cable?

---

### Post by ushaba on 2007-02-14
bump

---

