---
title: "D-Link DWL-G122 Guide?"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by Mr_Mason on 2007-07-23
Hello,

I have just received my Ubuntu 7.04 disks and i have installed them fine. It turns out i need a Linux driver for my D Link DWL-G122 H/W Version:B1 Wireless receiver, So i have looked around on the forum and tried some things out but had no look in getting it working. Is they a simple guide on the forum i can follow to get it working? If not can some one help me step by step to get it working?

My MSN live messenger if any one wants to help me 1 on 1: [email]mybeastlycomputer@hotmail.co.uk[/email]

Any help is appreciated.

---

### Post by Mr_Mason on 2007-07-24
I have solved this but thanks for all the help ;)

---

### Post by keirnna on 2007-07-25
> **Mr_Mason said:**
> Hello,

I have just received my Ubuntu 7.04 disks and i have installed them fine. It turns out i need a Linux driver for my D Link DWL-G122 H/W Version:B1 Wireless receiver, So i have looked around on the forum and tried some things out but had no look in getting it working. Is they a simple guide on the forum i can follow to get it working? If not can some one help me step by step to get it working?

My MSN live messenger if any one wants to help me 1 on 1: [email]mybeastlycomputer@hotmail.co.uk[/email]

Any help is appreciated.

How did you get this working?

---

### Post by ntom-taylor on 2007-08-24
Yes, you asked for help and then discovered how todo it but haven't told the rest of us

---

### Post by hadeshorn on 2007-09-02
Yes I would also like to know how please!

---

### Post by peebly on 2007-09-02
This wireless device works out of the box with Gutsy, but strangely when visiting certain websites it cuts out randomly and you have to unplug it and reboot ubuntu to get it going again.

---

### Post by Gage_AB on 2007-09-04
hey try this out mine worked .. except don't do the dll part.

[http://ubuntuforums.org/showthread.p...light=dwl-g122](http://ubuntuforums.org/showthread.p...light=dwl-g122)

---

### Post by thecoolcat on 2007-10-23
> **peebly said:**
> This wireless device works out of the box with Gutsy, but strangely when visiting certain websites it cuts out randomly and you have to unplug it and reboot ubuntu to get it going again.

Hmm. Doesn't work out of the box for me. Can you post your device-id? (lsusb)?

Thanks.

---

### Post by ~cyrus~ on 2007-10-23
Yes...the dwl-g122 works out of the box with the rt73 driver in Gutsy.

When I was on Fiesty, [this guide]("http://ubuntuforums.org/showthread.php?t=400236") worked for me for the rt73 driver.

Regards,

cyrus

---

### Post by thecoolcat on 2007-10-23
> **~cyrus~ said:**
> Yes...the dwl-g122 works out of the box with the rt73 driver in Gutsy.

When I was on Fiesty, [this guide]("http://ubuntuforums.org/showthread.php?t=400236") worked for me for the rt73 driver.

Regards,

cyrus

Hi Cyrus,

Thanks for your note. Can you post the rev no of your USB adapter? (lsusb|grep -i d-link)?

Regards.

---

### Post by ~cyrus~ on 2007-10-23
$ lsusb | grep -i d-link
Bus 004 Device 002: ID 07d1:3c03 D-Link System

---

### Post by thecoolcat on 2007-10-23
Thanks again cyrus. Mine is
Bus 001 Device 005: ID 07d1:[COLOR="Red"]3b01 [/COLOR]D-Link System

Very slightly different from yours. Let me do some research on this rev.

---

