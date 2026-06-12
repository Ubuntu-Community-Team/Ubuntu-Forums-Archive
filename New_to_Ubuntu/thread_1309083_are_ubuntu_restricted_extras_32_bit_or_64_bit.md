---
title: "are ubuntu restricted extras 32 bit or 64 bit?"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by Brian_Newbie on 2009-11-01
I just installed ubuntu 9.10 on my computer. brian@brian-laptop:~$ uname -a
Linux brian-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
brian@brian-laptop:~$

I installed the medibuntu repos as well as the libdvdcss2 and the w64 codecs with the following commands:

sudo aptitude install libdvdcss2 and sudo aptitude install w64codecs. 

What concerns me is that I installed the ubuntu restricted extras from that same website: [http://ubuntu-tutorials.com/2009/10/31/install-flash-and-multimedia-support-on-ubuntu-9-10-karmic-koala/](http://ubuntu-tutorials.com/2009/10/31/install-flash-and-multimedia-support-on-ubuntu-9-10-karmic-koala/)

When I used the command: "sudo aptitude install ubuntu-restricted-extras" from that page, it appears as though these packages are for 32 bit systems, not 64 bit systems.

Is this correct? - and if it is, will these 32 bit packages cause problems with my freshly installed karmic OS? 

I'd like to use all 64 bit packages that are stable and use 32 bit packages for those programs that have not passed beta testing yet.

---

### Post by zkriesse on 2009-11-01
A 32-bit package on a 64-bit system should not cause any problems.

---

### Post by oldos2er on 2009-11-01
Installing ubuntu-restricted-extras on 64-bit Ubuntu will give you 32-bit flash, as 64-bit flash is not in the repositories. You can run this script to install 64-bit flash: [http://ubuntuforums.org/attachment.php?attachmentid=128822&d=1253131938](http://ubuntuforums.org/attachment.php?attachmentid=128822&d=1253131938)

 Make sure you run the script *after* you've installed ubuntu-restricted-extras.

---

