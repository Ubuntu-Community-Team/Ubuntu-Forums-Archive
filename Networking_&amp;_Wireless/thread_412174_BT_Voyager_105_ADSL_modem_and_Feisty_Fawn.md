---
title: "BT Voyager 105 ADSL modem and Feisty Fawn"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by chriswyatt on 2007-04-17
Hi, I'm having trouble connecting to the internet after upgrading to Feisty Fawn, here is the output when I try to connect using ECIADSL-DOCTOR:

```
chriswyatt@chriswyatt-laptop:~$ sudo eciadsl-doctor
Password:
You are using linux kernel version 2.6.20-15-generic
Support for USB is OK
Preliminary USB device filesystem is OK
dabusb module is not loaded: OK
UHCI support is OK
OHCI support is not needed
/dev/ppp is OK
HDLC support is OK
HDLC support is OK (no bug)
Loading EZ-USB firmware... 
Process skipped .. no more needed
Loading the GlobeSpan firmware...
 ERROR reading interrupts                              
 Please Wait.. Synchronisation in progress [/]
```

I'm guessing it's probably a compatibility problem between the driver and the new linux kernel, though you'd think because it came from the official repositories that they'd work together.  I've tried reinstalling and reconfiguring ECIADSL to no avail.  Before, I used the ECIADSL driver from the Ubuntu repositories coupled with the usermode thingy from the maker's website.  I'm not too sure whether Ubuntu updated the ECIADSL driver when I upgrade to Feisty Fawn.

I'm quite sure it's not a connection problem as I can connect fine using Windows XP.

Thanks.

---

### Post by chriswyatt on 2007-04-17
Just found the answer to my problem from the forums on the makers website:

[URL="http://eciadsl.flashtux.org/forum/viewtopic.php?t=3247"]
http://eciadsl.flashtux.org/forum/viewtopic.php?t=3247[/URL]

---

### Post by chriswyatt on 2007-04-18
Wow, it worked, here is the link to the Debian package:

[http://eciadsl.flashtux.org/download/debian/etch/eciadsl-usermode_0.11-1_i386_with_synch_patch.deb]("http://eciadsl.flashtux.org/download/debian/etch/eciadsl-usermode_0.11-1_i386_with_synch_patch.deb")

First time I tried it (before I went to bed) it didn't work, tried it this morning and it connected fine :) .

---

### Post by proalan on 2007-04-19
cheers mate, was looking to a solution to this.

---

### Post by espresso on 2007-04-20
Help!! I'm a complete newbie to Linux. Can someone please explain exactly how to implement this patch?

Thanks in advance...

---

### Post by john_spiral on 2007-04-26
try:

**dpkg -i eciadsl-usermode_0.11-1_i386_with_synch_patch.deb**

Is this correct anyone?

---

