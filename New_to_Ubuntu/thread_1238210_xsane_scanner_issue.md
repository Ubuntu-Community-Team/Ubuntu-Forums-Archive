---
title: "xsane scanner issue"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by crabclaw on 2009-08-12
This my first time adding a peripheral to my ubuntu jaunty box. I want to add a CanoScan Lide 700F to Xsane and am coming up real short. 

I have not added a driver as I assumed it would just work with the Universal USB thing on most new USB devices.

I have never used a scanner on this computer before post or pre ubuntu.


Many thanks,

crabclaw

Found ubuntu supported scanners here

Found detailed scanner info [here]("http://www.sane-project.org/sane-backends.html#SCANNERS")

---

### Post by halitech on 2009-08-12
with the scanner plugged in and turned on, open a terminal and post the output of
```
lsusb
```

---

### Post by crabclaw on 2009-08-17
> :~$ lsusb
Bus 001 Device 003: ID 04a9:1907 Canon, Inc. 
Bus 001 Device 002: ID 0ac8:0321 Z-Star Microelectronics Corp. USB 2.0 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

The first one there is the Canon scanner but xsane will always choose the webcam over the scanner. Is there a way the unsupported hardware issue?

---

### Post by mikechant on 2009-08-17
Can you try with the Webcam disconnected, just to see if the scanner works at all? If that's OK then we can look at the selection issue (I'm sure there's a way to do this in xsane but I'm not at my Ubuntu PC at present).

Cannon scanners are generally well supported in Linux.

---

### Post by ahogg on 2011-08-03
I realize that this post isn't going to be of much help, but I have the same scanner and have yet to get it working.  It is my understanding that Canon has not released the architecture of that scanner to the SANE development team yet, so SANE can't talk to it.  Canon has also failed to do this with many other scanners.  While some Canon scanners work, I think it is a bit of an optimistic view to say that Canon scanners are well supported in Linux.  In fact, there are many Canon devices that aren't well supported in Linux.  It's quite clear that Canon is uncaring at best toward the Open Source community, and so we just have to wait to see what happens.  Once critical details become available from Canon, or are leaked out in some fashion about the architecture of that scanner and others, then the SANE team can begin talking to the scanner.  It's sad, because that scanner represents a great value.  Of course, it works nicely in "those we don't speak of." I can't tell you how much it kills me to say that.  But it's all worth it in the end.

If there is news stating the opposite, then I will gladly apologize for the rubbish.  Just please, somebody, help a brother out.  Show me how to get this paperweight alive in Linux.

---

