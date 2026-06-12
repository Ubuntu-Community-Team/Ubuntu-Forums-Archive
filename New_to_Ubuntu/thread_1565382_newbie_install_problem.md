---
title: "newbie install problem"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by stktek on 2010-08-31
I made a usb install and am trying to install on my Aspire one with a new hdd 500gig
When I boot up i get the following.
Can not mount /dev/loop1 on /cow

Help please

---

### Post by juil on 2010-09-01
I don't think you can boot from a usb....
just a burn it onto a disc...

---

### Post by anewguy on 2010-09-01
How did you make your USB installation?  Normally one would chose that option in Ubuntu or else use something like unetbootlin (I *think* that's what it is called).

Once you have that, if you set your boot order in the BIOS to try USB it should boot.

Dave

---

### Post by sikander3786 on 2010-09-01
> **anewguy said:**
> How did you make your USB installation?  Normally one would chose that option in Ubuntu or else use something like unetbootlin (I *think* that's what it is called).

Once you have that, if you set your boot order in the BIOS to try USB it should boot.

Dave

Yes it is unetbootin

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

It is pretty simple and a nice tool.

---

### Post by trikster_x on 2010-09-01
Just copying over the .iso file does not work with USB thumb drives.  Definitely use Unetbootin.  I have an aspire one as well that I installed 10.04 on with no problems at all.  I tried on an earlier version to manually create a bootable usb thumbdrive, and found out very quickly how many hours of frustration unetbootin will actually save people.

---

### Post by anewguy on 2010-09-01
I should probably add that I have an Acer Aspire One netbook as well and loaded Ubuntu 10.04 to it via USB having created the USB image with unetbootin (wasn't sure of the spelling in my first post).

---

