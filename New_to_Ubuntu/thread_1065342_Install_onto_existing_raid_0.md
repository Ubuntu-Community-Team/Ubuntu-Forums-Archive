---
title: "Install onto existing raid 0?"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by mrapoc on 2009-02-09
Hey

It was created entirely usin bios and integrated raid controller (not within windows)

Im using a maximus formula (asus) board

Ubuntu detects the two drives as seperate things :confused:

Any ideas?

---

### Post by avtolle on 2009-02-09
Does [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) give you any help?

Edit: Perhaps the one thing I gleaned from the link, and another link which got me there, is that one needs to use the alternate vs. the live CD for best results.

---

### Post by Gannon8 on 2009-02-09
I dont think you should use BIOS RAID.

The mdadm tool allows you to create RAID devices.
[http://www.linuxmanpages.com/man8/mdadm.8.php](http://www.linuxmanpages.com/man8/mdadm.8.php)

---

### Post by mrapoc on 2009-02-09
mdadm being fully compatible with ubuntu and windows alike?

how about fake raid?

any disadvantages over bios raid?

just after something to work for the two :confused:

---

### Post by mrapoc on 2009-02-10
Can anyone assist me into doing this mdadm thing?

If it really is that hard I suppose I could use a seperate disk for ubuntu :confused:

---

