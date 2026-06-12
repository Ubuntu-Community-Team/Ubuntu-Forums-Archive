---
title: "help with connecting usb WiFi adapter to ubuntu"
date: 2019-01-15
forum: Networking &amp; Wireless
---

### Post by eyefiles on 2019-01-15
my computer doesn't natively support wifi so i got a usb wifi adapter to use it
this is the one i got: [https://www.amazon.com/1200Mbps-Wsky-Wireless-802-11ac-Mac10-5-10-13/dp/B07F9JWY7X/](https://www.amazon.com/1200Mbps-Wsky-Wireless-802-11ac-Mac10-5-10-13/dp/B07F9JWY7X/)

when I connect it to the USB port in my computer , nothing happens. 
the network status at the top still says "cable unplugged".
I tried "lspci" in the terminal and it doesn't even show up. help? is it a driver issue? TIA

---

### Post by jeremy31 on 2019-01-15
If you have a USB adapter, post results for command ```
lsusb
```

---

### Post by eyefiles on 2019-01-16
> **jeremy31 said:**
> If you have a USB adapter, post results for command ```
lsusb
```

```

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0bda:b812 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 05dc:a81d Lexar Media, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

"Logitech Unifying Receiver" is my wireless keyboard.

---

### Post by jeremy31 on 2019-01-16
Moved to Networking
See [https://ubuntuforums.org/showthread.php?t=2410484&p=13831262#post13831262](https://ubuntuforums.org/showthread.php?t=2410484&p=13831262#post13831262)

---

### Post by chili555 on 2019-01-16
Jeremy has a perfect answer here: [https://askubuntu.com/questions/1049728/issues-installing-wifi-adapter](https://askubuntu.com/questions/1049728/issues-installing-wifi-adapter)

---

### Post by eyefiles on 2019-01-20
> **jeremy31 said:**
> Moved to Networking
See [https://ubuntuforums.org/showthread.php?t=2410484&p=13831262#post13831262](https://ubuntuforums.org/showthread.php?t=2410484&p=13831262#post13831262)


Sorry for the late reply, solution worked perfectly. It turns out "Realtek Semiconductor Corp" was the adapter, lol.Thanks lots.

---

