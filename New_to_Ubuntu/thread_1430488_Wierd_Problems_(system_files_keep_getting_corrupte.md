---
title: "Wierd Problems (system files keep getting corrupted?)"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by polandee on 2010-03-15
I'm not sure how to describe my problem. I have been using Ubuntu on this computer for over a year when all of the sudden it has been screwing up in some strange ways. When I turned my computer on yesterday, everything was fine. I then check a few websites and listen to some music. I did not download anything or go to any websites that I haven't been to a thousand times before. Both my music player and Firefox then stop working and I can't open up any new programs, so I restart my computer. It is unable to start, saying "Target File System doesn't have /sbin/init". I read up on how to fix that problem, and successfully (or so I thought) fix the problem by entering GRUB recovery mode and using the command "sudo fsck -y /dev/sda1" the computer then starts up with no sign of problems. I then do some typical things (check e-mail, music, etc) with the computer working fine. I assume the problem is fixed and leave for a few hours. When I come back, no programs work, even things as simple as gedit. I have to shut down the computer again. GRUB recovery mode "fixes" all the problems this time without me having to do any manual checks. Once again I can log in, and once again the computer is useless after a few hours. This last time I tried to turn on the computer I got a new error message about how the graphics were not working or connected and when I tried to run a file system check it just started spewing out gibberish. Please help.
**[]("http://ubuntuforums.org/showthread.php?t=611251") **

---

### Post by cgroza on 2010-03-15
i wold reinstall...

---

### Post by chaanakya_chiraag on 2010-03-15
I think this might be a hardware problem.  i.e. your hard drive is dying (I think).

---

### Post by quadproc on 2010-03-15
> **polandee said:**
> I'm not sure how to describe my problem. I have been using Ubuntu on this computer for over a year when all of the sudden it has been screwing up in some strange ways.

This does sound like a hardware problem.  The most obvious candidates are your system disk and the main memory.  Here are a few suggestions

1. Try using the "smartctl" program to check your main hard disk.
2. Run the memory tester (this is probably memtest86) instead of booting linux.
3. Boot from a different device such as a Live CD or a memory stick.
4. If you are overclocking then reduce to standard clock rates.
5. Check that the system is getting proper cooling.
6. Check the power supply voltages inside the computer.

If your memory has parity or some other form of error detection and it is the problem then you might find entries in the various system logs.  You will find those logs in /var/log; I would check dmesg, faillog, kern.log, messages, syslog, and perhaps Xorg.0.log.

quadproc

---

