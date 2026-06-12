---
title: "installation on striped raid (raid 0)"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by hetihe on 2011-05-03
11.04 "grub-install/dev/sda" failed
Hi,
tried to install 11.04 on raid 0 with two HDDs, but in the end of the installation process I got this message, it offered me also another place (supposedly "raid-place"", it had a long name) to install but no success. How to proceed? Do I need alternate CD to install from?
:(
timo

---

### Post by fredrik-fyksen on 2011-05-03
What kind of RAID controller do you have? If you use the motherboards "fakeRAID" it's better to use Ubuntu software RAID. It offers more flexibility, and lover risks for errors like this.

Guide to installing ubuntu software raid:
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by hetihe on 2011-05-03
> **fredrik-fyksen said:**
> What kind of RAID controller do you have? If you use the motherboards "fakeRAID" it's better to use Ubuntu software RAID. It offers more flexibility, and lover risks for errors like this.

Guide to installing ubuntu software raid:
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
hi,
I used motherboard´s bios'Raidmaker, I don't know whether it is called "fakeRAID".

---

### Post by fredrik-fyksen on 2011-05-04
That is a fakeRAID.. The cpu is used to controll the RAID. Then it's better to go the ubuntu fakeraid route. (follow my link from my other post)

-Sry for my english. Fyksen.

---

