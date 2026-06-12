---
title: "Is there some way to pre-define how I want the drive partitioned in the install...?"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by brucewagner on 2010-04-20
I am creating a "standard Ubuntu install" disk... using remastersys.

Is there any way to pre-define how I want the drive partitioned in the install...?

In other words, I want my "standard install" to create a 25GB partition for / and a 10GB partition as a swap, and the remainder of the drive (whatever size it is), as /home

Upon reinstalls...  I want it to do the same thing, but NOT format the /home partition.

It would be very difficult to talk remote users through this process.  I can't even use Remote Desktop to do it myself.... during the installation....  right?

Is there any way to make this automatic?

---

### Post by dearingj on 2010-04-20
> **brucewagner said:**
> 
It would be very difficult to talk remote users through this process.  I can't even use Remote Desktop to do it myself.... during the installation....  right?

Is there any way to make this automatic?

I know that with a standard Ubuntu desktop cd, you can enable remote desktop once the live environment is booted.

As for the rest of your question, you might find the answer by Googling the phrases "Automatic installation using Kickstart" or "automating the installation using preseeding". I think kickstart and preseeding are different ways of semi- or fully-automating the Ubuntu installation process.

---

