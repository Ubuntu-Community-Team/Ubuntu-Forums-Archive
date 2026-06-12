---
title: "How to connect 2 PC running Ubuntu?"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by LastWho on 2009-02-03
Hi,
i m trying to connect my pc to a laptop running both ubuntu 8.04!
SOS

---

### Post by jimmy the saint on 2009-02-03
connect how?  ssh?  to share files?  as a virtual desktop?

For ssh, you can get Putty from add/remove
for remote desktop, try the "remote desktop viewer" in the applications menu.
to share files you may have to install and setup samba if you are connecting from a windows machine.
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by candtalan on 2009-02-03
> **LastWho said:**
> Hi,
i m trying to connect my pc to a laptop running both ubuntu 8.04!
SOS

If you have a network, using LAN ethernet cables which has a router, you can connect both PCs to the router using ethernet patch cables.

If you do not have a router, but want to connect the two computers together only, you can use an ethernet cable going directly from one to the other, however, I believe the cable is not an ordinary patch cable, it will need to be a 'crossed' cable (I think pins 2 and 3 are reversed at one end) to allow a mutual send and receive facility.

---

### Post by lkraemer on 2009-02-05
Here is how I have done it with a crossover cable and
vsftd running on one machine, with filezilla on the other.

[http://ubuntuforums.org/showthread.php?t=1031300&page=2](http://ubuntuforums.org/showthread.php?t=1031300&page=2)

lkraemer

---

