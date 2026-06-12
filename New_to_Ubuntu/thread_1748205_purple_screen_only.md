---
title: "purple screen only"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by oxygenfarm on 2011-05-03
I was setting up an old computer already running Ubuntu 10.04 for my 10-year-old grandson, loading it with many scientific programs and setting him as new user, when I suddenly got the inspiration to run Update Manager. Mistake.

Update Manager listed many new/better programs, so I said 'why not'.

After a reboot I now get only the Ubuntu purple screen, with nothing showing anywhere. The mouse pointer is still active.

I hope that a Live CD will allow me to roll back whatever happened to my graphics, but beyond that vague wish I'm scoreless. Help! I would not like to repeat all the downloads.

---

### Post by dniMretsaM on 2011-05-03
It's possibly a driver/graphics card issue. Boot with the Live CD and run lspci in terminal. Post the output.

---

### Post by oxygenfarm on 2011-05-03
Here it is:

ubuntu@ubuntu:~$ lspci 
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge 
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge 
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) 
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) 
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) 
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) 
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge 
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) 
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50) 
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74) 
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev a4)

---

### Post by oxygenfarm on 2011-05-03
Suddenly a message popped up telling me that 11.04 is available (while I'm running from the CD) and then a download tool started downloading, on its own volition. Ghosts?

---

