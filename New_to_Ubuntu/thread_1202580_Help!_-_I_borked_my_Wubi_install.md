---
title: "Help! - I borked my Wubi install"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by blues2use on 2009-07-02
I'm a month in with Wuubi so be kind...

I edited the /boot/grub/menu.lst file in ubuntu Wubi trying to get my LVPM transfer to boot and borked my Wubi boot. I know which line I changed in /boot/grub/menu.lst while I was in ubuntu Wubi but I have no idea how to fix it since I can't boot via Wubi. I can only boot to XP now and the Ubuntu (Wubi) boot option gives me a "File 15 - file not found" error. Until I can boot into Wubi, I don't know how to fix what I messed up.

As a side issue, my Wubi install was what I transferred via LVPM to a 100gb ext3 partition (I'm running a single 320gb hard drive with XP/Wubi and, hopefully, my LVPM install). The transfer took place without a problem but the grub Error 17 wouldn't allow me to boot to it. I am unable to get past the "Error 17 cannot mount selected partition" when I try to boot to the LVPM partition. I have the boot_info_script results stored on my Wubi desktop and, using those and reading around the forum, decided to try to edit the /boot/grub/menu.lst file to fix the Error 17 problem...bad move on my part...

Your help would be most appreciated.

As a fair warning - I'll be back and asking about how to fix my LVPM error 17 install problem... ;-)

Thanks in advance

---

### Post by blues2use on 2009-07-02
SOLVED: apparently, grub had added: uuid EC5C389C5C38638C and removed: root ()/ubuntu/disks from the title sections of /boot/grub/menu.lst

Here's what I did to fix the "Error 15 file not found" when trying to boot into Ubuntu (Wubi):

booted to XP and edited the menu.lst file in /ubuntu/disks/boot/grub/ menu.lst file by removing the uuid EC5C389C5C38638C line in the title sections and replacing it with: root ()/ubuntu/disks

HTH

I'm actually kinda proud of myself (total newbie)...took some reading and searching and trying different things, but I finally figured it out... ;-)

---

