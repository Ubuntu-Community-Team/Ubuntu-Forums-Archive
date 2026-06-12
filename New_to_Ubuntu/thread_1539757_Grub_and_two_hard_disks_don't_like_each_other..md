---
title: "Grub and two hard disks don't like each other."
date: 2010-07-26
forum: New to Ubuntu
---

### Post by Windows Nerd on 2010-07-26
So, I am NOT using Ubuntu, but the problem is not relative to Ubuntu. I just use this forum because of the bigger user base and faster responses.

Anyways, so after a week with this problem, youd think I would give up, I shall not. 

I am now, after reinstalling 4x, instead of having a Grub error, I am now just left with a blinking underscore.

No error.

Can anyone please help me reinstall Grub *legacy *from a liveCD? The system itself is installed just fine. I am using two hard drives, which is where I think I am screwing up. sdb is where I installed /, sda is larger, and therefore is mounted as /home.  

If you want anymore information just ask...

Scott

Here is the thread on the Arch Linux Forum if you want to take a look at what I have done so far:

[https://bbs.archlinux.org/viewtopic.php?id=101753](https://bbs.archlinux.org/viewtopic.php?id=101753)

---

### Post by confused57 on 2010-07-26
Here's a thread for reinstalling grub legacy, using a live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by oldfred on 2010-07-27
If you have grub2, you need to totally uninstall that before reinstalling grub.

HowTo: Revert from grub2 to Legacy Grub or grub to grub2 kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

---

### Post by Windows Nerd on 2010-07-27
I followed the guide and installed grub to sdb. I still get the blinking cursor. 

Maybe it is because the BIOS is not set to boot to that drive, as the secondary hard drive was added in just recently. I cannot see exactly how you do this as my BIOS does not give me any option to change which drive to boot to.

---

### Post by oldfred on 2010-07-27
Do you have SATA drives, if so the BIOS should include a way to set drives. Often separate from the selection of boot order of CD, Floppy or HD. Then maybe even a different page is which HD. Others have it inside the HD selection.

If you still have PATA and an old BIOS you have to set jumpers on the drives or if using cable select reverse drives on cable. Primary master is what BIOS boots. Some drives have jumpers for master, slave & and then master with slave.

---

### Post by Windows Nerd on 2010-07-27
Nevermind, I have figured it out: I installed Grub onto the MBR of the first hard disk then had menu.lst point to the second one. It works, and as a bonus I learned a lot about Grub (and how to chroot :))

---

