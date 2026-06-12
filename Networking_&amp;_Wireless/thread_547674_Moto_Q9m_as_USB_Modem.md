---
title: "Moto Q9m as USB Modem"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by sanicki on 2007-09-10
Using Kubuntu 7.04. Have been successful getting various aircards and xv6700 mobile phone working as USB modem via KPPP. Now trying Moto Q9M.

Generally just able to do a 'dmesg | grep tty' and use the result. This time I see:
PocketPC PDA converter now attached to ttyUSB0
...immediately followed by:
PocketPC PDA converter now disconnected from ttyUSB0
...and KPPP doesn't see anything at /dev/ttyUSB0 or /dev/usb/ttyUSB0.

Is this a Motorola driver issue? Anyone know if installing Moto4Linux would make this work?

UPDATE: Have tried the VZAccess Manager Linux version (which I just found out about but would have saved me time with our aircards!) Unfortunately the Moto Q is not yet supported. Our VZ business rep is checking their development roadmap for an ETA on it. Will update when I have their timeframe. Meanwhile any other suggestions welcome.

---

### Post by sanicki on 2007-12-28
Got to love the internets. Over at Qusers.com I found the following post:
[http://www.qusers.com/forum/viewtopic.php?t=11935&sid=99f516f09b2a88]("http://www.qusers.com/forum/viewtopic.php?t=11935&sid=99f516f09b2a88")
I can't find the file to make it autoload (any help, Ubuntuphiles?) but doing a "sudo modprobe usbserial vendor=0x22b8 product=0x7001" worked as a one-off.

---

### Post by sanicki on 2008-04-28
FYI, Verizon doesn't explain very well that there is a $15 month charge for tethering that you must opt for in order for this to work. I feel like I've been trying to fix a light switch in a house without power!

---

