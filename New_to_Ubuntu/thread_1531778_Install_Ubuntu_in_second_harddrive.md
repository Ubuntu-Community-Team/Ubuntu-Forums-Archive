---
title: "Install Ubuntu in second harddrive"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by cazador31 on 2010-07-15
I am running windows 7. I want to install Ubuntu 10.04 on a second  harddrive. I am new at this and would like to know the correct way to do  it. Easy instructions would be appreciated since I am new to Ubuntu

Thank You

---

### Post by fooman on 2010-07-15
in my opinion,  since you are installing onto a separate hard drive....the safest way would be to shutdown and disconnect your windows drive.

then restart,  and install ubuntu onto your spare drive.

when it completes,  and you have run all updates....shutdown and reconnect your windows drive.  set your bios to boot to ubuntu, and when you get there....open a terminal and type or copy/paste:

```
sudo update-grub
```that should find the windows drive and add it to the grub menu,  allowing you to dual-boot.

hope that helps.

---

### Post by QIII on 2010-07-15
+1.

After you have done this a few times, disconnecting the Windows drive is probably unnecessary because you will understand how to make sure you are putting it on the right drive.

But do it as described to avoid accidentally writing over your Windows installation.

By the way.  If you have SATA drives, don't disconnect the cables on the motherboard side.  The headers have a nasty habit of coming off with the cable and the headers are VERY hard to get back on without breaking pins.  Disconnect the cables from the disk side, like you would with the power cable.

---

