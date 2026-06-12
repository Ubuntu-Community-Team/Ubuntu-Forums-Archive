---
title: "Two boot menus using Ubuntu 10.4 LTS"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by steveintianjin on 2010-10-31
Hi 

I have recently installed Ubuntu on my ASUS laptop using the Wubi installer. When I boot up, I get two boot screens. The first says:

Please select the OS to start

Microsoft Windows XP Professional
Ubuntu

I select Ubuntu and then I get the Grub 2 menu giving me different kernel options, recovery, and a Windows XP option again.

The problem is that the first menu only stays up for a few seconds and then boots into Windows, the default entry. Unless I sit with my finger poised over the arrow key to select Ubuntu I often miss the chance and have to reboot from the Windows logon screen and pay more attention. :)

I have read the Grub 2 community docs, but these do not seem to refer to the first menu.
I've tried editing the default entry in /etc/default/grub but, of course, that didn,t work either.
I've searched the forums at length and not found a post about the issue

My questions are:

Can I get rid of the first Windows/Ubuntu menu and just have the Grub 2 menu appear when I boot, or;
Can I edit this first pesky menu to change the timeout duration (perhaps so that it doesn't timeout)?

Thanks in advance for your assistance

---

### Post by Megaptera on 2010-10-31
I think if you install startupmanager in your wubi Ubuntu install it allows you to change the default timing:

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

### Post by P4man on 2010-10-31
Im no wubi expert, but that first menu isnt grub is it? I think its windows bootloader, and you should configure it in windows. IIRC, its been a while, right click my computer/properties.. and then somewhere well hidden in advanced. I dont remember the exact location. Alternatively, edit c:\boot.ini and change the timeout there.

All that said..best solution is not using wubi.

---

### Post by dhiman33 on 2010-10-31
Yep, don't install ubuntu using wubi. It makes it slow. Just make another partion to make space for ubuntu and install it there. Makes things less complex.:guitar:

---

### Post by steveintianjin on 2010-10-31
Thanks for your replies, everyone. The problem is solved.

I will get around to installing the non-wubi version when I get time. You think it's faster? Wow. I'm still marveling at the speed difference between Ubuntu and Windows XP!

Anyway, thanks again.

---

### Post by waynefoutz on 2010-11-01
> **steveintianjin said:**
> Thanks for your replies, everyone. The problem is solved.

I will get around to installing the non-wubi version when I get time. You think it's faster? Wow. I'm still marveling at the speed difference between Ubuntu and Windows XP!

Anyway, thanks again.

yes it faster, and more stable. Your Wubi install is nothing more than a big file written in your Windows file system. It's not a real drive. If that file gets corrupted, a nice power interruption would do it, your Ubuntu install is destroyed. Wubi is great for testing and trying out Ubuntu without the commitment, it's not meant to be a permanent, long term install.

---

### Post by Trandok on 2010-11-01
Since ubuntu is installed onto Windows, you are essentially using Windows while in ubuntu, so in order for the system to boot, windows needs it's bootloader. You cant just replace it with grub, Windows is not that friendly.

---

### Post by P4man on 2010-11-01
Dont expect miracles performance wise. Disk IO is a bit faster than with wubi, but its not an enormous difference. It is however, much more reliable and flexible.

---

