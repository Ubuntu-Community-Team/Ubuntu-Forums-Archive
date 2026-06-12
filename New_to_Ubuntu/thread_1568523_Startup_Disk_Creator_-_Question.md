---
title: "Startup Disk Creator - Question?"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by mapes12 on 2010-09-05
I have a Netbook with no optical drive but it can boot from a USB drive. I've successfully booted it with a USB stick that had a bootable version of UBU 10.04 created from the .iso install file via Startup Disk Creator. 

Now, I need to do completely and securely wipe the HDD and I want to use either of these utilities:-

[dBan]("http://www.dban.org/")
[KillDisk]("http://www.killdisk.com/")

I know the latter is a windows .exe but unsure what format dBan is.

My question is: How do I get this onto a USB bootable disk?

I've downloaded the dBan .iso but Startup Disk Creator will not load it as a source? I've also looked at Unetbootin but the documentation states that it only supports Linux installation .iso's?

On my old machine which had an optical drive I would just burn a disk and off you go.

Any help greatly appreciated.

Mark

---

### Post by coffeecat on 2010-09-05
If you've got a bootable USB stick with Ubuntu 10.04, you've already got a utility that comes with that which will securely wipe the whole of the HD, including the MBR and partition table.

Boot up with the USB drive. Open a terminal. With a netbook you will only have one HD, sda, but let's be sure we're wiping the correct drive. :? Do:

```
sudo fdisk -l
```If that shows you that the size of the sda HD is the same as your internal HD, and the size of sdb is your bootable USB, then fine. Now from the terminal:

```
sudo shred -zvn 7 /dev/sda
```... and go away for a few hours. :wink:

That will give you 7 passes plus a final eighth pass with zeroes. The first and seventh are random, the others are patterns of digits which the output will tell you about. That's complete overkill, of course. If you want to leave out the final zeroing, omit the -z option. To change the number of passes, change the number. For more information, type...

```
man shred
```... in the terminal.

---

### Post by C.S.Cameron on 2010-09-05
dd will also do a good job of wiping a disk:

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

