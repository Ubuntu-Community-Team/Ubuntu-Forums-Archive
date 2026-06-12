---
title: "USB not working after Update to 8.04"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by nuclearj on 2009-06-05
I up graded from Gutsy to Hardy and had some problems with the start up but after me bumbling around, it fixed itself!  But that is not what I need help with today...

My usb ports do not "work".  My amateur diagnosis is that when something is plugged in the computer sees that it's there but does nothing to mount it, a ipod or flash drive for example.  But my keyboard and mouse have had no problems and they are connected through USB.

here is my lsusb
```

Bus 004 Device 005: ID 090c:1000 Feiya Technology Corp. Flash Drive
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 045e:009d Microsoft Corp.
Bus 001 Device 001: ID 0000:0000

```

Anyone have any ideas on where to start?

---

### Post by hanzj on 2009-08-08
when you write "8.04", do you mean "9.04"?

---

### Post by sandyd on 2009-08-08
Theres already something wrong from what i see. what is "Bus 001 Device 003: ID 045e:009d Microsoft Corp." there should be a device type after that. however, its missing.

---

### Post by sandyd on 2009-08-08
p.s. can you do this?
unplug your flash drive , and run ```
ls /dev 
``` copy all the output from that command and save it to your desktop as dev-1.txt. then, plug your usb device into the computer, and run ```
ls /dev 
``` save thhe output from that onto your desktop as dev-2.txt . Then ```
cd ~/Desktop
diff dev-1.txt dev-2.txt
``` post the output plus the two files (dev-1.txt, dev-2.txt) here

---

