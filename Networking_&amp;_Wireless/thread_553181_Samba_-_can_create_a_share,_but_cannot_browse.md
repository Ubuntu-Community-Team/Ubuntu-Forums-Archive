---
title: "Samba - can create a share, but cannot browse"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by dcwilliams on 2007-09-17
My apologies if this has already been posted, I tried searching through the forums but I could not find this particular problem.

I have a small network Ubuntu 7.04 i386  (fresh install yesterday), a BSD Box, a Windows laptop and a network storage device for backups.

I have installed Samba on my BSD box, and I can read and write to all shared folders to/from Windows and BSD, and both Windows and BSD can read/write my network storage device.

Ubuntu is the exception. I can share a folder on my Ubuntu box, which both BSD and Windows can read and write to, but Ubuntu is unable to browse the network. If I click Places > Network Servers I see the workgroups (my work laptop uses a different one), and if I click on one workgroup I can even see the computers listed (but not the other workgroup). If I click on a computer, it gives me an "Unable to" error.

I have gone so far as to copy my smb.conf from my BSD box to my Ubuntu box, and make the appropriate changes, but the same result. I can share a folder which everyone can use, but I can not browse the network or manually mount a share on another system.

Dave

---

### Post by sisco311 on 2007-09-17
have you created a samba account?
if not:```
sudo smbpasswd -a username
```

---

### Post by dcwilliams on 2007-09-17
Yes, I created an account.

---

