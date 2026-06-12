---
title: "Linux Foundation 1.1 root hub"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by coolbrook on 2009-10-02
I recently discovered that my [Tyan Thunder LE-T (S2518[COLOR="White"].[/COLOR])](ftp://ftp.tyan.com/manuals/m_s2518_120.pdf) has an onboard USB header (J80) that I can use for the front panel of my ATX case.  I hooked it up, tried my USB flash drive (to no avail) and I figured that I was out of luck.  For kicks, I attached a Logitech gamepad and to my surprise the turbo light lit up when I pressed the button.  Once again there appears to be a problem since I can't map it on gfceux (NES emulator) like I could on the USB ports at the back of the motherboard.

```
steven@LEONARDO:~$ lsusb
Bus 001 Device 004: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 001 Device 002: ID 0d8c:0103 C-Media Electronics, Inc. Turtle Beach Audio Advantage Micro
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

It's my belief that the USB header is third device detected above.  There's power delivered, but no apparent communication.  I'll love to get this working and need your help.

---

### Post by cariboo on 2009-10-02
Check the connection to make sure it is connected properly, on some of the cases I own there is a separate plug for each pin on the header. On others, the ground plug is separate.

What is the output of dmesg when you plug in a usb device:

```
dmesg | grep tail -n10
```

will show you the last 10 lines of dmesg.

---

### Post by coolbrook on 2009-10-03
No output, but with just **dmesg**, here are the last 10 lines.

```

[195726.915505] Unknown OutputIN= OUT=eth0 SRC=169.254.7.171 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
[195726.915824] Unknown OutputIN= OUT=eth0 SRC=169.254.7.171 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
[196027.331419] Unknown OutputIN= OUT=eth0 SRC=169.254.7.171 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
[196027.331855] Unknown OutputIN= OUT=eth0 SRC=169.254.7.171 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
[196327.746530] Unknown OutputIN= OUT=eth0 SRC=169.254.7.171 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
[196327.746938] Unknown OutputIN= OUT=eth0 SRC=169.254.7.171 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
[196437.898970] Unknown OutputIN= OUT=eth0 SRC=169.254.7.171 DST=169.254.255.255 LEN=260 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=240 
[196437.899213] Unknown OutputIN= OUT=eth0 SRC=169.254.7.176 DST=169.254.255.255 LEN=260 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=240 
[196628.161991] Unknown OutputIN= OUT=eth0 SRC=169.254.7.171 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
[196628.162324] Unknown OutputIN= OUT=eth0 SRC=169.254.7.171 DST=169.254.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58
```

---

### Post by GeorgeVita on 2009-10-03
Hi **coolbrook**
from the manual (your 1st post link)> 2.1 Front Panel Connector (J80)
Your chassis will usually come with connectors to install onto the motherboard, such as HDD and Power LEDs. The Front Panel Connector (J80) has been implemented for such purposes.
This is NOT a 'front USB' connector!

You can try: > 2.12 USB Port Headers (J72, J73)
These headers can be used to connect additional USB ports. If you intend to install front-side USB ports, please check if your chassis is compatible for such a configuration. Tyan does not provide front-side USB
cables.
Warning: be sure for the V+ and GND pins, do not reverse them!

Regards,
George

---

### Post by coolbrook on 2009-10-03
> **GeorgeVita said:**
> Hi **coolbrook**
from the manual (your 1st post link)
This is NOT a 'front USB' connector!

You can try: 
Warning: be sure for the V+ and GND pins, do not reverse them!

Regards,
George

Hello George.  I made a mistake in saying J80 instead of 72/73.  I'm on the computer now with everything but the front USB working.  Thanks.

---

### Post by coolbrook on 2009-10-07
Up

---

