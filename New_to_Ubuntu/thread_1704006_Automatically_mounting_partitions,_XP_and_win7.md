---
title: "Automatically mounting partitions, XP and win7"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by ferdz_30 on 2011-03-10
Hi everyone. I'm currently using Ubuntu 10.04 and I want my XP partition to be "automatically mounted" each time I open Ubuntu 10.04 so that I don't have to do it manually (by going to COMPUTER > right clicking the drive > mount)??

I'm a little new to Ubuntu, I've been using it for like 3 months now. Please help me with this so that I'll be able to instantly open my XP folder links(on Ubuntu Desktop) immediately without having to mount the XP/win7 drive over and over each time I open Ubuntu.

Please give a step-by-step process.

Thanks. I'll be hoping for a reply. ):P

---

### Post by pressko on 2011-03-10
Hi,


I can help u with the easiest way i know (cuz i'm a ubuntu noob 2 ) . Go to Applications -> Ubuntu Software Center - > and search for NTFS Configuration Tool -> install it - > type your password -> mark Enable write support for internal device - > reboot - > that's all ;)

---

### Post by ferdz_30 on 2011-03-10
> **pressko said:**
> Hi,


I can help u with the easiest way i know (cuz i'm a ubuntu noob 2 ) . Go to Applications -> Ubuntu Software Center - > and search for NTFS Configuration Tool -> install it - > type your password -> mark Enable write support for internal device - > reboot - > that's all ;)
Hey Pressko, thank you for that quick reply and answer. It works now. Thanks for the help. =)

---

### Post by AbhiJais on 2011-03-10
Hi,
even you can try modifying /etc/fstab for that purpose.

add  the following line in the above file.

/dev/<device name>         <mount point>         auto         defaults        0       0

Here:
<device name> partition of hddrive like sda0/1/2 or so.
<mount point> any empty directory but i would suggest to make it under /media like /media/windows or so.
you can replace auto with the type of file system of drive like ntfs or so. if you know about fstype.

That's all and each time you start your pc, it would get mounted automatically.
:)

---

### Post by ferdz_30 on 2011-03-10
tnx, tnx, tnx. =) Thanks to all. I'm learning from you guys. Again, thanks for the concern.

---

