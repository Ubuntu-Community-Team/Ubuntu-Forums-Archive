---
title: "HDD mechanical failure"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by qwerty1105 on 2009-08-05
Not sure if this is where to post this, so let me know if it needs moved.

I have an external HDD (Western Digital 250GB).  This morning it quit.  All I hear is the head clicking.  It will not connect to my machine at all.  I tried it on another machine, (running Win xp) and it did the same.  I am guessing it is not a power issue.  Any thoughts?  I only need to get the data off.  I am not concerned about the HDD at all, just the data.

I have received quotes from places online ranging anywhere from $250 to $1000 to get the data off.  I don't know which ones are good or even if I should send it out.  I would hate to get scammed...  :confused:

---

### Post by khelben1979 on 2009-08-05
I suggest you add the companys to this thread so we (or I) can have a look at them.

How old is the harddrive and have you ever tried to replace the usb cable? (I doubt it will help though, I think they are pretty cheap)

---

### Post by wizard10000 on 2009-08-05
The ones that charge $250 will run software-based utilities that you can run yourself for free, tell you the data can't be recovered and pocket your money.

The ones who charge $1000 or more will remove the platters from your hard drive in a clean room, install the platters in a good drive, extract your data, write it to DVD and send it to you.

How to keep from getting scammed?  If you're certain the drive has a mechanical failure (and the actuator clicking is most certainly a mechanical failure) ask the recovery company if they disassemble the drive in a clean room to get the data off it.  No clean room, no data recovery on failed hardware.

I have recovered data from a drive by replacing the controller board with one from an identical drive but that's only worked for me once.

---

### Post by Jerry N on 2009-08-05
I suppose it needs to be said again:  NEVER NEVER NEVER have your important data stored in only one place, no matter whether you are running Linux, Windows, Xenix, or Commodore Pet!!!

Jerry

---

### Post by halitech on 2009-08-05
start planning the funeral, that puppy is dead. You could try the freezer trick, it might allow you to get some of the data off but the more it reads the drive, the warmer it gets so time is of the essence if you try it.

Put the drive in an airtight bag (ziplocks work good) then put it in the freezer at least 12 hours. Then take the drive out, wait 20-30 minutes then hook it up to the computer. If the computer gods are looking favorably on you, you will get it to connect and get some data off. If not, dig a hole a bury it.

---

### Post by Warren Watts on 2009-08-05
> **Jerry N said:**
> I suppose it needs to be said again:  NEVER NEVER NEVER have your important data stored in only one place, no matter whether you are running Linux, Windows, Xenix, or Commodore Pet!!!

Hmm..  I had better backup all that Commodore Pet data I have stored on 8" floppies...! j/k

Seriously though, I agree.  Backup, backup, backup

---

### Post by XCan on 2009-08-05
> **qwerty1105 said:**
> Not sure if this is where to post this, so let me know if it needs moved.

I have an external HDD (Western Digital 250GB).  This morning it quit.  All I hear is the head clicking.  It will not connect to my machine at all.  I tried it on another machine, (running Win xp) and it did the same.  I am guessing it is not a power issue.  Any thoughts?  I only need to get the data off.  I am not concerned about the HDD at all, just the data.

I have received quotes from places online ranging anywhere from $250 to $1000 to get the data off.  I don't know which ones are good or even if I should send it out.  I would hate to get scammed...  :confused:

$1000 still sounds pretty cheap. You need to check the companies' background and their track records, Google comes to mind. When it comes to important data, it is probably worth it for you to spend a little more money on your only chance to recover the data. However, if we are talking about physical damage to the platters themselves, all the money in the world won't save you.

---

### Post by lkraemer on 2009-08-05
qwerty1105,
Here is an idea that might be of help.  A good friend of mine, who
is a University Professor had an External USB Drive that wouldn't
work when it was plugged into a USB port.  He was wanting the DATA
REAL BAD.  He had no backup......

I suggested he bring me the drive, which I promptly disassembled,
removed the 2.5" IDE Drive, plugged in my 3.5" to 2.5" IDE Adapter,
connected the drive to my Secondary IDE Cable and booted my 
Ubuntu Desktop.  The drive was detected by my BIOS and mounted.
All the Data was there.  I promptly burned all the data files to
DVD's, and backed the drive up on another larger drive.  Then I
deleted the partition with gparted, created a new partition, formatted
the new partition, and dumped the data files back on the drive.

After inserting it back in the External case, I plugged the USB cable
in my Desktop, and the drive showed up with the data files.

Yours may be IDE or SATA, but it would be worth a try to see if maybe
it will work via a direct connection to your Motherboard.

But, Head Clicking typically means a defective drive.  Although I
did have one Corporate Laptop that was clicking, and I powered it down
and Slapped the Laptop on the Left side real hard with my left hand
and it booted and worked the remainder of the day.  Go figure!

Good Luck.

lkraemer

---

### Post by synapsys on 2009-08-05
Clicking usually means the head has crashed into the platters. Fixing this is very expensive. I guess the question is.... How important is the data on that drive?

---

### Post by tgalati4 on 2009-08-06
Sometimes it's a power issue.  Perhaps your USB port is not putting out enough power.  Try another machine.  If your hard drive has an external port for 5V power, find a source for 5V power.

By cracking the case and removing the drive and using an adapter cable to a standard IDE cable, the higher power of the ribbon cable can sometimes overcome a sticky platter or worn motor.

---

