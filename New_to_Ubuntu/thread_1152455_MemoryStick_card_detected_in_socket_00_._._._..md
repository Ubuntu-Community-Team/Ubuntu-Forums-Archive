---
title: "MemoryStick card detected in socket 0:0 . . . . ?"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by jakwriter on 2009-05-07
I'm running Hardy on a 1.6GHz Centrino dv 5220 HP laptop.  I'm having trouble figuring out the card reader though.  My camera uses a Sony Memory Stick ProDuo.  After swimming through forums trying to find a solution I picked up this command . . .

 dmesg | tail -n10

 . . . and its output. This is with the card in the reader.

[13218.668726] Outbound IN= OUT=wlan0 SRC=192.168.0.64 DST=41.222.70.203 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=13974 DF PROTO=TCP SPT=59207 DPT=45353 WINDOW=5840 RES=0x00 SYN URGP=0 
[13218.669372] Outbound IN= OUT=wlan0 SRC=192.168.0.64 DST=41.222.70.203 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=22937 DF PROTO=TCP SPT=59208 DPT=45353 WINDOW=5840 RES=0x00 SYN URGP=0 
[13221.664745] Outbound IN= OUT=wlan0 SRC=192.168.0.64 DST=41.222.70.203 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=22938 DF PROTO=TCP SPT=59208 DPT=45353 WINDOW=5840 RES=0x00 SYN URGP=0 
[14414.613562] Outbound IN= OUT=wlan0 SRC=192.168.0.64 DST=41.222.70.203 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=59076 DF PROTO=TCP SPT=47567 DPT=45353 WINDOW=5840 RES=0x00 SYN URGP=0 
[14417.610464] Outbound IN= OUT=wlan0 SRC=192.168.0.64 DST=41.222.70.203 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=59077 DF PROTO=TCP SPT=47567 DPT=45353 WINDOW=5840 RES=0x00 SYN URGP=0 
[14417.610715] Outbound IN= OUT=wlan0 SRC=192.168.0.64 DST=41.222.70.203 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=24711 DF PROTO=TCP SPT=47568 DPT=45353 WINDOW=5840 RES=0x00 SYN URGP=0 
[14420.610456] Outbound IN= OUT=wlan0 SRC=192.168.0.64 DST=41.222.70.203 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=24712 DF PROTO=TCP SPT=47568 DPT=45353 WINDOW=5840 RES=0x00 SYN URGP=0 
[14559.231864] tifm_core: MemoryStick card detected in socket 0:0
[14731.920187] tifm0 : demand removing card from socket 0:0
[15063.144211] tifm_core: MemoryStick card detected in socket 0:0

What does this mean?

My problem is that I don't know what to do with this info, or where to go from here.  Do I need a driver?  Is it now time to learn more handy, Ubuntu tricks? 

Hope springs eternal.

---

### Post by coffeeaddict22 on 2009-05-07
It looks like it's picking it up.  When you've got the card in, what does ```
lsusb
``` show?

---

### Post by llamabr on 2009-05-07
This is unlikely to be a driver issue.  What exactly is it not doing that you want it to do.

And, with dmesg, the idea is to plug it in, wait a few seconds, and then run that command again:

```
dmesg | tail -10
```

And post the output.  If you plugged it in an hour ago, it will already be useless, since it's a real time log.

---

### Post by jakwriter on 2009-05-08
lsusb

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

The card reader is built in, should it show up as USB?

dmesg | tail -n10

[   73.003785]  domain 0: span 03
[   73.003789]   groups: 02 01
[   89.653258] usb 3-2: new low speed USB device using uhci_hcd and address 2
[   89.675275] usb 3-2: configuration #1 chosen from 1 choice
[   89.781326] usbcore: registered new interface driver hiddev
[   89.787360] input: Logitech Trackball as /devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2:1.0/input/input9
[   89.792454] input,hidraw0: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:1d.2-2
[   89.792474] usbcore: registered new interface driver usbhid
[   89.792481] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  179.246781] tifm_core: MemoryStick card detected in socket 0:0

And two minutes later

dmesg | tail -n10

[   73.003785]  domain 0: span 03
[   73.003789]   groups: 02 01
[   89.653258] usb 3-2: new low speed USB device using uhci_hcd and address 2
[   89.675275] usb 3-2: configuration #1 chosen from 1 choice
[   89.781326] usbcore: registered new interface driver hiddev
[   89.787360] input: Logitech Trackball as /devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2:1.0/input/input9
[   89.792454] input,hidraw0: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:1d.2-2
[   89.792474] usbcore: registered new interface driver usbhid
[   89.792481] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  179.246781] tifm_core: MemoryStick card detected in socket 0:0

What is all this telling me?

---

### Post by tonsai on 2009-05-08
I think this is a known problem with the Texas Instruments Card reader. Have a look at this forum, I'm using a HPnc6320 and having similar problems: [http://ubuntuforums.org/showthread.php?t=797031&referrerid=830476](http://ubuntuforums.org/showthread.php?t=797031&referrerid=830476)

---

### Post by jakwriter on 2009-05-08
Thanks for the tip.  At first glance that thread is looking helpful.

---

### Post by jakwriter on 2009-05-08
> **llamabr said:**
> This is unlikely to be a driver issue.  What exactly is it not doing that you want it to do.



Although the Memory Stick is getting picked up, it doesn't seem to be mounting.  I can't access it at all.

I've found a patch (tifm_ms.c), although I'm not clear on what it will do, or what to do with it.  Any tips are appreciated.

---

### Post by jakwriter on 2010-10-08
Of course 10.04 solved it.  Card reader jumps all over the card, didn't have to do anything but insert the card.

I love Ubuntu, and everyone who makes it possible.  Gives me hope for the human race.

---

