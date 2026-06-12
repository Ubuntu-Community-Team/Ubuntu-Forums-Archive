---
title: "Uninstall WUBI/ Install Linux Mint or Ubuntu"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by brandoncolorado on 2009-01-01
Hello,

I am using 8.10.  I have it installed via WUBI within Windows Vista.  I have had some problems including free space availability and a number of minor bugs.  I would like to start from scratch.  Could I uninstall WUBI, and then install Linux Mint or Ubuntu on a partition?  If not, would it be best to install Linux first and then Windows, or to install Windows and then Linux?

---

### Post by f37u5g0d on 2009-01-01
It is about 100 times easier to install windows first and then linux.  Linux is friendly windows isn't.  I think you are a little bit confused.  WUBI creates a file inside the windows filesystem (on the windows partition) that ubuntu uses as a hard drive similar to a virtual computer.  No partitioning is done and you can make that file as large or as small as you want when running the wubi installer.

If you install ubuntu normally onto the hard drive (like using a live cd or live usb) then you partition the hard drive.  At that point as well you can make the linux file system or "/" (root) as large or as small as you want.

You don't have to uninstall wubi first if you don't want to.

---

### Post by brandoncolorado on 2009-01-01
Thanks for the help.  I do understand the way WUBI works, but I unfortunately did not set a large enough file large enough.  After some research, making the WUBI file size larger retroactively seems like a hassle.  If I understand correctly, an installation via WUBI also has some performance drawbacks.

---

### Post by stoogiebuncho on 2009-01-01
> If I understand correctly, an installation via WUBI also has some performance drawbacks.

Yeah, I would say a real partitioned install is best if you're serious about Linux Mint / Ubuntu.

As you may know, it's very easy to uninstall a WUBI install - just go to Windows and to the Add/Remove Programs area and you'll be able to get rid of it from there.

Then download the .iso of whatever distro you want to install and boot it up.  

You can actually migrate your WUBI install to a full install, so you won't lose your settings or anything:
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?")

---

### Post by Sef on 2009-01-01
> Thanks for the help. I do understand the way WUBI works, but I unfortunately did not set a large enough file large enough. After some research, making the WUBI file size larger retroactively seems like a hassle. If I understand correctly, an installation via WUBI also has some performance drawbacks.

You could uninstall WUBI, then reinstall it with a bigger file.

---

