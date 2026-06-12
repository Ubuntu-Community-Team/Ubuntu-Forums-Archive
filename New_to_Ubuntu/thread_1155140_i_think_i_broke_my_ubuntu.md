---
title: "i think i broke my ubuntu"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by VioletsPie on 2009-05-10
Ubuntu doesn't load after the splash screen ever since I installed a ton of stuff from add/remove in one session. I tried restore, fdisk check, etc but now it just is blank after the splash screen. 

Jaunty 64 on HP Pavilion DV6000

---

### Post by Redache on 2009-05-10
It might just be simpler if you backed up your data using the Live CD and then reinstalled Jaunty.

---

### Post by Bölvaður on 2009-05-10
> **VioletsPie said:**
> Ubuntu doesn't load after the splash screen

We need to know what is the problem so you'll need to provide us with as much and as detailed information as you can possibly gather.

What makes you think it doesnt load?
Is there any text?
Is the screen blank?
Do you get graphics on the live cd?
Or by pressing E in grub (you might need to press ESC while booting when it asks you) and add "xforcevesa" at the end of the boot command, press esc and then B to boot again... no graphics?
In the same menu as before (grub) can you reach the command line interface login screen if you boot with the recovery mode?

---

### Post by VioletsPie on 2009-05-14
Grub returns 'file not found', trying live cd now. 

What happens is the ubuntu splash screen appears, the bar loads, then the screen changes a bunch of times from black to blue to black as if it's trying to load, then stops at blue.

Yep, live cd boots fine.

---

### Post by VioletsPie on 2009-05-16
bump? Let me restate my problem: 

After installing a lot of stuff in one session (maybe a ton of games etc.) Ubuntu no longer displays after boot. The instructions above that had me go into grub and run that command in E returned "file not found." The live CD works fine. 

What happens is the splash screen loads just fine and the bar fills up and then it seems to "try" to load as the harddrive thinks and the screen changes to different colors like it's trying to boot, but eventually stops. 

If reinstallation is the only option, what is the best way to install over the old partition?  If there is another way out without having to reinstall, that'd be appreciated. 

-VP-

---

### Post by sailor2001 on 2009-05-16
on boot-up..hit "esc" and then down arrow to next option for repair 'x'

---

### Post by WatchingThePain on 2009-05-16
Might be a broken xserver.
There's a command that you can run from recovery mode called xfix.

---

### Post by VioletsPie on 2009-05-17
thanks for all your help but no dice. I am going to reinstall this time the 32-bit, I read that there's no advantage to 64-bit other than if you have more than 4 gigs of ram anyway.

---

