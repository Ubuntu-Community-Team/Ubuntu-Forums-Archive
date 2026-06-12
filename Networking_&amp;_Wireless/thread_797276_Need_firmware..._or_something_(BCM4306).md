---
title: "Need firmware... or something? (BCM4306)"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by Fzang on 2008-05-17
I'm currently running ubuntu from a live CD but the wireless doesn't work

It says

"Broadcom B43 wireless driver" at the section "hardware drivers"

When I mouse over it, it says 

"while this driver itself is free software, it relies on proprietary firmware which cannot be legally shipped with the operating system. Your hardware will not work without the firmware"

Now what do I do? Do I put this firmware on the desktop and then press "enable" and it will work out, or something? I'm pretty newb at this

---

### Post by spd106 on 2008-05-17
If you have access to a wired connection then just install the b43-fwcutter package and it will download and install the firmware for you.

Otherwise you'll have to fetch the firmware from [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
Get the wl_apsta_mimo version as that's the one expected by the b43 driver. You will still need to to extract this using the b43-fwcutter tool so that will have to be installed as well.

There should be a couple of guides around the forums showing you how to do this.

This page will be useful too, [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by Fzang on 2008-05-17
I sniffed around on the internet and I found this, I believe it's the firmware thing but not completely sure because I haven't used any linux stuff before

---

### Post by Fzang on 2008-05-17
I can't extract the tar for fwcutter, wtf?

In the guide it says:

If you are using the old deprecated bcm43xx driver, follow these instructions.

Use version 006 of bcm43xx-fwcutter.
Download, extract the bcm43xx-fwcutter tarball and build it:

wget [http://bu3sch.de/b43/fwcutter/bcm43xx-fwcutter-006.tar.bz2](http://bu3sch.de/b43/fwcutter/bcm43xx-fwcutter-006.tar.bz2)
tar xjf bcm43xx-fwcutter-006.tar.bz2
cd bcm43xx-fwcutter-006
make
cd ..


Of course I don't have internet on my ubuntu machine yet...so I pasted the link to my laptop and downloaded the tarball, then transfered to my ubuntu

Now when I enter the line:

tar xjf bcm43xx-fwcutter-006.tar.bz2

It says "file or directory not found". I put the file on the desktop

What am I doing wrong??

---

### Post by Fzang on 2008-05-17
Bump my gumb

Or something...

---

### Post by Ayuthia on 2008-05-17
You can try this [link]("http://ubuntuforums.org/showthread.php?t=779754").  There is a section for those without an internet connection.  Hope it helps.

---

### Post by Ayuthia on 2008-05-17
> **Fzang said:**
> I sniffed around on the internet and I found this, I believe it's the firmware thing but not completely sure because I haven't used any linux stuff before
It is actually a Broadcom wireless driver for Windows.  It is used for NDISwrapper which is another option for you.  I would try the firmware route first and if you don't like it or it isn't working well, you can switch.

---

### Post by Fzang on 2008-05-18
Hey I did the firmware thing, though the guide was a bit cluttered...

But now it detects my network!:).... It just won't connect...:(

It hangs at "attempting to connect"

What now...?

---

### Post by Fzang on 2008-05-18
Aaaanyways, I've tried installing the driver as well and at both options it says "hardware found" and "enabled" and stuff

But it just won't connect!

---

### Post by Ayuthia on 2008-05-18
> **Fzang said:**
> Aaaanyways, I've tried installing the driver as well and at both options it says "hardware found" and "enabled" and stuff

But it just won't connect!
Sorry about the cluttered post.  I'll try to clean it up sometime.

You might try to see if you can connect to another channel on your router.

---

### Post by Fzang on 2008-05-21
Topic revived

Seriously, any help? I don't want linux if it hates me

---

### Post by Fzang on 2008-05-21
Bump

Any solutions or should I forget linux?

---

