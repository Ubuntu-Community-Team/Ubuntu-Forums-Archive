---
title: "Can't fit Ubuntu on EeePC 2G Surf"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by crawshs on 2011-02-06
Hi. Sorry if this has already been covered elsewhere. I have been asked by a friend to see if I can get a better OS on their eeepc (they're currently running XP which is horrid).

It's an old one, with only a 2Gb SSD. When I download and try to install the Ubuntu Netbook version, it needs more than 2Gb to install. Are there any skinnier versions about?

Many thanks in advance!

---

### Post by Daveth on 2011-02-06
I would take a look at this first off
[HTML]http://appstogo.mcfadzean.org.uk/eeepc.html[/HTML]

---

### Post by Miljet on 2011-02-06
You might look at DSL(Damn Small Linux). I think it is only 50 MB.

---

### Post by Old_Grey_Wolf on 2011-02-06
My wife had a eeePC 701. I couldn't install the XP service pack because it didn't have enough SSD space left. I finally installed Ubuntu on it by adding a SD card. If I remember correctly, I got an 8GB SD card for about US$30. SD cards are probably less expensive now.

---

### Post by crawshs on 2011-02-06
Thanks for all the helpful info everyone.

Ok, so it looks like the best route to go would be to stick in a chunky-ish SD card (4Gb enough?) and bung an OS on that.

Being a Linux noob, is that straightforward? Do I need to edit startup or config files to get the netbook to do that? If I run the Ubuntu install, can I just tell it to install to the SD card and bingo?

I'm reasonably techie, but not in linux space....

---

### Post by Old_Grey_Wolf on 2011-02-06
> **crawshs said:**
> Thanks for all the helpful info everyone.

Ok, so it looks like the best route to go would be to stick in a chunky-ish SD card (4Gb enough?) and bung an OS on that.

Being a Linux noob, is that straightforward? Do I need to edit startup or config files to get the netbook to do that? If I run the Ubuntu install, can I just tell it to install to the SD card and bingo?

I'm reasonably techie, but not in linux space....

If you use the manual partitioning in the installer it should not be difficult. It shouldn't require editing config files, etc. You will probably need to install to the sdb partition.

---

### Post by crawshs on 2011-02-09
> **Old_Gray_Wolf said:**
> If you use the manual partitioning in the installer it should not be difficult. It shouldn't require editing config files, etc. You will probably need to install to the sdb partition.
Ok, I've managed to install it to an SD card but am struggling to get the damn machine to successfully boot. I've changed the BIOS to only boot from the SD card but I'm wondering whether some sort of config file needs to be changed to point the boot loader to the correct partition?

---

### Post by crawshs on 2011-02-09
not sure if this helps but the following is the boot argument;

BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic-pae root=/dev/sdc1 ro quiet splash

---

### Post by crawshs on 2011-02-09
ok i changed it to 

BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic-pae root=/dev/sdb1 ro quiet splash

at the boot menu, which allowed it to boot successfully.

Problem is it's not persistent, where is the file sotred and how do i edit it to keep the change permanently. 

Ugh - sorry for the stupid noob questions...

---

### Post by P4man on 2011-02-09
Check the link in my signature below how to make it permanent. Short story, edit ```
/etc/default/grub 
```then run ```
sudo update-grub
```.

BTW, you're doing incredibly well for a noob!

---

### Post by crawshs on 2011-02-10
Thanks for the encouragement P4Man. Playing with Linux feels like I've been thrown back to the early 80's when I was scratching my head over MS-DOS, not that I don't love it, just that I know so little about it.

Mind you, although my background is mainly Windows related, the basic principles don't really change.

All sorted now although it wasn't that file that needed to be edited, it was all consolidated into a boot menu file, the name of which escapes me. But managed to edit the correct entry so it boots every time now.

Many thanks to everyone for their help and suggestions.

---

### Post by P4man on 2011-02-10
> **crawshs said:**
> Thanks for the encouragement P4Man. Playing with Linux feels like I've been thrown back to the early 80's when I was scratching my head over MS-DOS, not that I don't love it, just that I know so little about it.

Mind you, although my background is mainly Windows related, the basic principles don't really change.

All sorted now although it wasn't that file that needed to be edited, it was all consolidated into a boot menu file, the name of which escapes me. But managed to edit the correct entry so it boots every time now.

Many thanks to everyone for their help and suggestions.

If you edited /boot/grub/grub.cfg, then you did it wrong. It will work until the next time you have a kernel upgrade and that grub config file gets overwritten. You have to edit the script that generates grub.cfg, and that is /etc/default/grub. Then execute the script to generate the grub.cfg file by running

```
sudo update-grub
```

Anything else will give you trouble down the line.

---

