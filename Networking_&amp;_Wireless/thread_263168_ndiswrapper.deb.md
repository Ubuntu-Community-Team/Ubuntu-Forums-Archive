---
title: "ndiswrapper.deb"
date: 2006-09-22
forum: Networking &amp; Wireless
---

### Post by Olzen on 2006-09-22
Hi
Could someone please hint me where to download the ndiswrapper.dep file or mail it to me. (dapper)

The system i'm trying to fix does not have make installed, or internett currently available. So I need a precompiled.

[email]gkfolsen@gmail.com[/email]

regards
O

---

### Post by compwiz18 on 2006-09-22
[http://archive.ubuntu.com/ubuntu/pool/main/n/](http://archive.ubuntu.com/ubuntu/pool/main/n/)

you can download it from there

---

### Post by K.Mandla on 2006-09-22
It's also on the Ubuntu CD.

Edit: Here's one that's zipped. Extract it with *tar -xvfz ndiswrapper.tar.bz2*.

Watch your [dependencies]("http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils").

---

### Post by Neobuntu on 2006-09-22
Are you talking about just getting it installed?

In that case it already is (in Dapper.) At least it is available from the install CD.

If your are talking GUI. Then after installing it on the command line (if wireless is your only way online at the moment) then install ndis-gtk for point and click ease (after Kernel upgrades.) Put your XP wireless drivers in a directory off your /home/~you~ directory.

---

### Post by Olzen on 2006-09-23
Thanks for your help! Solved my problem.

I had only wireless Internet available and no Ubuntu cd. Downloaded ndiswrapper.deb and windows driver on a windows laptop. Copied the files to the Ubuntu laptop, extracted the driver and used ndiswrapper as described on tihs community, -Worked like a charm

System: Dell Inspiron 8200, truemobile(Broadcom 42xx).

O


PS: There should be some kind of sticker computer producers could put on their product notifying the customer that the computer only contains components with Liux support.

---

### Post by Neobuntu on 2006-10-02
Great, your welcome.

Don't forget to install "ndis-gtk" and put those XP drivers under a directory like "wifi" in your /home/*you* directory. This way, when a kernel upgrade automatically comes through, you can point and click the XP drivers quickly and with ease.

Also people, note that your (XP driver needed) device might have a reverse engineered driver/modules in the works and install with the next auto Kernel upgrade. If your system locks up you may have the two drivers trying for the same device. It may also not work for you and thus you will want to blacklist it and use ndiswrapper (in modules so that it works on boot.)

Finally, you may just need to reboot. Yes you don't **have** to reboot and you can do other technical restarts, but rebooting is user friendly. Just know that may be all you have left to do.

Of course if you really want to save time, just online order yourself a $10 device that is reported to work with (k)ubuntu. Then you have zero driver issues.

---

### Post by douradinhos on 2007-06-14
tks, very usefull

---

