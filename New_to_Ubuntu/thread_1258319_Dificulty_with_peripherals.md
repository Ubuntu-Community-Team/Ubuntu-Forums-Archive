---
title: "Dificulty with peripherals"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by Keith A on 2009-09-04
I am absolutely frustrated by my attempts to get ubuntu working on my machine. I have searched the forum for threads with similar problems to mine and have managed to come up with this info. I had to photograph it because I can't access my printer with ubuntu. 
 
[IMG]http://ubuntuforums.org/D:machine hardware sep 09[/IMG]
 
I cannot access any of my periherals except the flatbed scanner.
 
Sound
mobile broadband
printer
monitor (It has a display but I cannot change its resolution, or aspect ratio)
 
None of these work.
 
I am really thinking of uninstalling ubuntu and trying to re-install but I can't find out how to do that. any help will be appreciated. Thanks
Keith
Oh dear, th epicture did not work. Here is what it should be:-
 
Bus 001: Device 004 ID 1058:1010 Western digital Technologies, Inc.
Bus 001: Device 001 ID 1d6b:002 Linux Foundation 2.0 root hub
Bus 004: Device 003 ID 12d1:1001 Huawei Technologies Co. Ltd. E620 USB Modem
Bus 004: Device 002 Canon, Inc PIXMA iP3000x Printer
Bus 004: Device 001 ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003: Device 002 ID 0c45:602c Microdia Clas Ohlsen TWC 30Xop WebCam
Bus 003: Device 001 ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:2005 Hewlett-Packard Scanjet 3570c
Bus 002 Device 001: ID 1d6b:001 Linux Foundation 1.1 root hub
 
~S lshw -C network
description: Ethernet interface
physical id: 2
logical name: pan0
serial: a6:84:4f:e5:b7:d9
capabilities: ethernet physical
configuration: broadcast=yes driver=bridgedriverversion=2.3 firmware=N/A mulitcast= yes
 
Keith

---

### Post by Paqman on 2009-09-04
Hi, please don't start multiple threads, it'll just make it more difficult for people to help you.

[Original thread here]("http://ubuntuforums.org/showthread.php?p=7899050#post7899050").

---

### Post by halitech on 2009-09-04
Printer - [http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA-iP3000](http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA-iP3000)

should work fine with the Gutenprint driver
```
sudo apt-get install cups-driver-gutenprint
```

What video card do you have? post the output of
```
lspci
```

your modem info is here - Huawei Technologies Co. Ltd. E620 USB
[http://ubuntuforums.org/showthread.php?t=776306](http://ubuntuforums.org/showthread.php?t=776306)

---

