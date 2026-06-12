---
title: "I broke my computer. Oh god."
date: 2010-03-09
forum: New to Ubuntu
---

### Post by Ryasaurus on 2010-03-09
Okay..so I tried to install Jolicloud to a USB drive. Everything worked perfectly, but I think it installed GRUB on my machine instead of the USB drive.

When I boot up Jolicloud, I get a GRUB error. It says the file cannot be found. Grub rescue>. So then, I looked it up and tried a bunch of stuff, but it didn't work.

So I tried to boot up Windows, on my SSD. When it tries to boot up, I get ERROR 21. And then nothing else. I can't press any keys or anything.

I need to fix this soon..any ideas?

---

### Post by 3rdalbum on 2010-03-09
I would try the procedure for reinstalling GRUB in Ubuntu. You will need to install it to the SSD so it will boot Windows.

(use the forum search or Google for 'reinstall grub' - I am posting from my phone).

---

### Post by Toddus on 2010-03-09
Let me make sure I understand the question first. Your grub is getting an error when you boot-up ubuntu? If that is the case, if you have a live cd you could try:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

---

### Post by Ryasaurus on 2010-03-09
I'm not using Ubuntu, though Jolicloud is based off of UNR. Anyway, I can't even access Jolicloud. It says there is a GRUB error, and it won't let me do anything about it. I don't care about losing my Jolicloud installation. It's my Windows installation I'm worried about. Even though I installed Jolicloud to my USB drive, it somehow affected my SSD, I believe.

EDIT: would reseting the BIOS solve this problem? Or not?

---

### Post by Toddus on 2010-03-10
> **Ryasaurus said:**
> I'm not using Ubuntu, though Jolicloud is based off of UNR. Anyway, I can't even access Jolicloud. It says there is a GRUB error, and it won't let me do anything about it. I don't care about losing my Jolicloud installation. It's my Windows installation I'm worried about. Even though I installed Jolicloud to my USB drive, it somehow affected my SSD, I believe.

EDIT: would reseting the BIOS solve this problem? Or not?

Well, if you are worried about your windows files, you can run ubuntu right from the live cd and access your other file partitions and copy your windows partition onto something...
Although it sounds like you can't even get that far without receiving a boot error.
You could try resetting your bios, I don't think that would effect your partitions, but I also don't think it would solve your problem. Bios just indicates performance settings for hardware and boot priority so if you reset it shouldn't do anything.

---

### Post by bodhi.zazen on 2010-03-10
What version of Windows ?

Do you have a recovery disk ?

---

### Post by Toddus on 2010-03-10
> **bodhi.zazen said:**
> What version of Windows ?

Do you have a recovery disk ?

I was going to suggest this as well, but it didn't sound like he/she was even able to boot anything...?

Yes, if you have a windows installation disk, boot it, and repair the partition of windows.

---

### Post by stevenh512 on 2010-03-10
Sounds to me like you installed GRUB to the hard drive's MBR instead of the USB drive. If I understand how GRUB works, it won't boot without the files it needs in your /boot partition so if those files are on your flash drive instead of your HD you might not be able to boot Windows by reinstalling GRUB. Find an old DOS or Win9x boot disk (or a recovery disk for your version of Windows), you might be able to find a disk image online and just write it to a floppy (using dd in Linux or something like WinImage in Windows). I'm not 100% sure because it's been years since I've done a Windows install, but you might even be able to do this with your Windows install CD if you can get to a command prompt.

Whatever the case, your boot disk has to have a copy of FDISK.EXE on it. Boot from the disk and enter this at the command prompt:

FDISK /MBR

This will replace the MBR on your hard drive without disturbing the partition table, so assuming nothing else is broken this should get you back into your Windows install.

---

