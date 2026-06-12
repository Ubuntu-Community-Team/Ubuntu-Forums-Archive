---
title: "drive authentication"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by bipinbaglung on 2009-03-04
i had set auto authentication at mount time but now i want to make it manual and how can i make it to ask password every time for authentication

---

### Post by DBrocks on 2009-03-04
Well you would have to remove the line that mounts the drive from the file /etc/fstab
Drives can only be mounted with SUDO, so, removing it from /etc/fstab effectively password protects it. If you need more help, post the contents of /etc/fstab.

---

### Post by bipinbaglung on 2009-03-04
i want to mount drives other than filesystem and system have to ask password every time for authentication

---

### Post by DBrocks on 2009-03-04
As I said, to mount a drive, you need to use sudo password. If you feel this is not enough, and you want complete drive encryption, look into truecrypt. Truecrypt encrypts any disk of your choice. You can choose to set aside a "vault" for encryption, or encrypt an entire disk. There was a nifty site I had open, but can't seem to find the link to it. Ill post it if i find it.

---

### Post by bipinbaglung on 2009-03-08
this is written in fstab





# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=ed9a2c3e-cc7a-432e-bc53-e5936eec5e31 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda10
UUID=e39456d4-90f8-4f80-9c87-2980f1d2f14d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by bipinbaglung on 2009-03-14
i cant make it as i want

---

### Post by DBrocks on 2009-03-15
> **bipinbaglung said:**
> i cant make it as i want
Please be more specific.

---

