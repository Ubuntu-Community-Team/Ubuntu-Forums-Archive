---
title: "LAMP on USB?"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by ornothaloapq on 2010-10-30
Does a ubuntu live USB drive contain the apache and mysql and other Internet type programs?

---

### Post by v1ad on 2010-10-30
no, not unless it is a Ubuntu Server cd.

---

### Post by ornothaloapq on 2010-10-30
Could that be put onto a USB and then booted from?

---

### Post by v1ad on 2010-10-30
yes it can, 

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[http://www.ubuntu.com/server/get-ubuntu/download](http://www.ubuntu.com/server/get-ubuntu/download)

remember to get the one u need, 32 bit or 64.

---

### Post by v1ad on 2010-10-30
also i just remembered that Ubuntu Server does not boot live.

you would need to add them manually to a Ubuntu image.... unless you install the server to the usb. and remember it will be in CLI mode.

if u want a desktop install ubuntu onto a usb. and then boot into it and install lamp and whatever else you need.

---

### Post by ornothaloapq on 2010-10-30
I thought you couldnt add programs to a live session even with persistence.

---

### Post by v1ad on 2010-10-31
not live. if u format the usb as ext4 and actually use it as a drive and install Ubuntu onto it. with only the ext partition and set it as the mount point /

---

