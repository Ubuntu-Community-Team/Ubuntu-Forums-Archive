---
title: "Forgot password, can't see grub menu"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by ryank76nz on 2011-05-08
I have a horrible combination of problems it seems. 

I have forgotten my password and am trying to reset it. I've found various instructions for resetting it that involving pressing ESC when you get to the grub menu, except it doesn't show up on my PC.

In a howto for 'how to get the grub prompt', I see I have to edit a file (which I can't do as I don't have my password) that isn't actually there: /boot/grub/menu.lst.

Could someone help please?

---

### Post by lisati on 2011-05-08
*Thread moved to **Absolute Beginner Talk**.*

Which version of grub are you using? Recent versions of Ubuntu use [grub2]("https://help.ubuntu.com/community/Grub2"), which doesn't use the menu.lst file.

---

### Post by yetiman64 on 2011-05-08
> **ryank76nz said:**
> I have a horrible combination of problems it seems. 

I have forgotten my password and am trying to reset it. I've found various instructions for resetting it that involving pressing ESC when you get to the grub menu, except it doesn't show up on my PC.

In a howto for 'how to get the grub prompt', I see I have to edit a file (which I can't do as I don't have my password) **that isn't actually there: /boot/grub/menu.lst.**

Could someone help please?

You are likely using grub2 which uses /boot/grub/grub.cfg (I suspect you are not on Jaunty anymore as indicated by your profile :)). You don't edit grub.cfg directly either anymore.

Try using the **shift** key to get the grub menu on boot. Then when the grub menu comes up you can choose a recovery (or single) boot to reset the password.

---

