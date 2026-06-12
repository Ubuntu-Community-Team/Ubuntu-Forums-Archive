---
title: "Shutdown issue"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by ~sHyLoCk~ on 2009-07-21
Ok a quick n00bish question. I installed ubuntu jaunty in my external hdd [seagate] and everything works fine! I shutdown using the shutdown option. The next time I boot from it, it gives me a lot of "Device descriptor error read/64 -110" errors. So I go to windows and run chkdsk /F and boot into windoze a couple of times [I have for 3 NTFS drives on the same external hdd and 2 ext3 one each fr root and home.] After doing this a couple of times things go back to normal and I can boot using my external hdd just fine. Is there a proper way of shutting down your external hdd so that I wouldn't have to face this problem everytime I boot?

---

### Post by c0mput3r_n3rD on 2009-07-21
> **~sHyLoCk~ said:**
> Ok a quick n00bish question. I installed ubuntu jaunty in my external hdd [seagate] and everything works fine! I shutdown using the shutdown option. The next time I boot from it, it gives me a lot of "Device descriptor error -110" errors. So I go to windows and run chkdsk /F and boot into windoze a couple of times [I have for 3 NTFS drives on the same external hdd and 2 ext3 one each fr root and home.] After doing this a couple of times things go back to normal and I can boot using my external hdd just fine. Is there a proper way of shutting down your external hdd so that I wouldn't have to face this problem everytime I boot?

Unmount the drive everytime before removing.  As well, you can run the Ubuntu disk check, when at startup press esc to enter boot menu, and run the file check (fsck I think it is).

---

### Post by ~sHyLoCk~ on 2009-07-21
> **c0mput3r_n3rD said:**
> Unmount the drive everytime before removing.  As well, you can run the Ubuntu disk check, when at startup press esc to enter boot menu, and run the file check (fsck I think it is).

I unmount all the NTFS partitions before shutting down/rebooting. But I can't unmount[obviously] the /home and /root partitions. Thanks for your reply though, will try fsck.

---

### Post by lavinog on 2009-07-21
Does your external drive connect with a eSata connector or usb?

---

### Post by ~sHyLoCk~ on 2009-07-21
> **lavinog said:**
> does your external drive connect with a esata connector or usb?

usb

---

### Post by ~sHyLoCk~ on 2009-07-22
Well any ideas? I really am worried that my HDD might get damaged if I continue using ubuntu on it which is presumably causing improper shutdown.

---

### Post by dk06 on 2009-07-22
Similar USB & External HDD error codes, possible fix:

[http://www.linux-archive.org/gentoo-user/312366-external-usb-hdd-device-descriptor-read-64-error-62-solved.html](http://www.linux-archive.org/gentoo-user/312366-external-usb-hdd-device-descriptor-read-64-error-62-solved.html)

[http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg18313.html](http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg18313.html)

[URL="http://ubuntuforums.org/showthread.php?t=1091237"]
[/URL]

---

### Post by ~sHyLoCk~ on 2009-07-22
> **dk06 said:**
> Similar USB & External HDD error codes, possible fix:

[http://www.linux-archive.org/gentoo-user/312366-external-usb-hdd-device-descriptor-read-64-error-62-solved.html](http://www.linux-archive.org/gentoo-user/312366-external-usb-hdd-device-descriptor-read-64-error-62-solved.html)

[http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg18313.html](http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg18313.html)

[URL="http://ubuntuforums.org/showthread.php?t=1091237"]
[/URL]

Thanks mate for taking the time to go through my post! But sadly none of that works! I don't use any other USB device except for my external HDD.

---

### Post by dk06 on 2009-07-22
I'm sorry those didn't help, I've been googling the error code & finding similar ones related to USB & boot  errors where grub is erroring out but nothing like you're saying.

If you can give some more detail, maybe I can help

---

