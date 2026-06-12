---
title: "tricky password recovery"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by Knacker on 2011-05-13
I've been away from a computer for years and can't recall the password. Complication is that I seem to have also reduced the grub menu to nothing at all, so I can't get into it to do the password change trick that I recall can work in these situations. Can someone suggest another course of action? Is there any way to get to grub prompt besides hitting Esc at start? If the answer is no, then what else should I consider doing to recover/change passwords?

I'd ideally like to be able to change both my administrative user password and my root password. Not sure what else to add...the computer is running karmic. 

Any help would be much appreciated -- the quicker/simpler the easier. I don't have a install disk, but could get one if that's the only way. 

Many thanks!

---

### Post by yetiman64 on 2011-05-13
> **Knacker said:**
> I've been away from a computer for years and can't recall the password. Complication is that I seem to have also reduced the grub menu to nothing at all, so I can't get into it to do the password change trick that I recall can work in these situations. Can someone suggest another course of action? Is there any way to get to grub prompt besides hitting **Esc** at start? If the answer is no, then what else should I consider doing to recover/change passwords?

I'd ideally like to be able to change both my administrative user password and my root password. Not sure what else to add...the computer is running karmic. 

Any help would be much appreciated -- the quicker/simpler the easier. I don't have a install disk, but could get one if that's the only way. 

Many thanks!

The escape key was used in the original grub (grub-legacy) try the **shift** key and you may get the grub menu with grub2 (it will depend on the system you have installed, try both methods). Don't just tap it once, after the bios menus finish, press it down and hold it down until the grub menu comes up.

Also here is a link for resetting the passwords from psychocats.net if needed: [http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

---

### Post by jtarin on 2011-05-13
I would suggest a Live CD and a CHROOT environment.

---

### Post by sidzen on 2011-05-14
See yetiman64 for getting into the grub menu, then
compliments *anticapitalista*:

Try this at grub menu.

1. Append &#8216;init=/bin/bash&#8217; at the end of line (no ' ')
2. Press Enter
3. Type mount -n -o remount,rw /  (at prompt)
4. passwd
5. Follow steps to give yourself a new root password
5. reboot

---

### Post by Knacker on 2011-05-14
AH! Grub2: forgot about that. Thanks, everyone! Working like a charm. :)

---

### Post by Knacker on 2011-05-14
Okay, I now have root and my main user/administrative passwords...but user keyring is still locked with what I'm guessing is the old password. Do I just need to delete this? Is it possible to change keyring password with the passwords I have now?

---

### Post by jtarin on 2011-05-14
This is beginnning to seem more like a hack of someone's system and I for one feel uncomfortable about using this forum for this. At the very least take it out of the Beginners Forum. There are other places to find this information if you really want/need it. My two cents.

---

### Post by bapoumba on 2011-05-15
Closed for review.

Edit: will remain closed.

---

