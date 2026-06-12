---
title: "Ubuntu won't boot from hard disk???"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by justinblakeyoung on 2009-04-20
Well I just got back from fry's with some new memory (of course I picked up the wrong sticks so I'll be going back to get different ones tomorrow!). Well while I had my case open, I decided to have a good look at the DDR that was already there so I'll be able to get the right ones when I go back. I popped one of them out, took a look and put it back in. Well when I went to restart, I got my usual dell splash screen but then just a blinking curser. I tried restarting several times before I popped in my Ubuntu boot disk and that finally worked. I really can't figure out why it's not booting from my HD- any ideas??

---

### Post by boblemur on 2009-04-20
first: look in your bios to see if your hard disk is detected. if not you probably bumped the power cord out of it when you were looking in your computer.

if it is found, then make sure the boot order is correct.

if both of them are correct, boot off the live cd and see if you can find/mount the hard disk partitions of your installed ubuntu.

if you can do that then try repairing grub. and reboot without the cd.

post any errors you get along the way :)

---

### Post by justinblakeyoung on 2009-04-20
> **boblemur said:**
> first: look in your bios to see if your hard disk is detected. if not you probably bumped the power cord out of it when you were looking in your computer.

if it is found, then make sure the boot order is correct.

if both of them are correct, boot off the live cd and see if you can find/mount the hard disk partitions of your installed ubuntu.

if you can do that then try repairing grub. and reboot without the cd.

post any errors you get along the way :)


Man is my face red. I had a flash drive in my usb port and it was trying to boot from that. I took it out and bingo no more problems. Jeeze I'm embarassed. Thanks for your help!

---

