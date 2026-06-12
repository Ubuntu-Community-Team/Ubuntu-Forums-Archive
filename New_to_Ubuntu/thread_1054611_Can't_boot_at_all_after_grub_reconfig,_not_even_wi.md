---
title: "Can't boot at all after grub reconfig, not even with live cd or vista repair disk"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by stuhlmuller on 2009-01-29
Thanks in advance for taking a look at this thread

I'm running a Dell e1505 Laptop with dual-boot Ubuntu and vista. After reinstalling vista, I had to reconfigure grub. However, this killed my ability to boot. After the initial Dell boot screen comes up, it goes to a black screen with the blinking dash in the top left corner...and that's all! :/ I've tried to boot a vista repair disc and ubuntu live cd but neither of these cd-roms can be booted and once again the system goes to the black screen. I even tried changing the boot order in the BIOS menu but that leads to the same dismal fate. I'm stumped! Does anyone know what the problem might be and if there's a solution? Thanks.

---

### Post by Raccoon1400 on 2009-01-29
What happens if you hit F12 when it's booting to get the one time boot device menu?

Is there any new hardware that you recently added?
I've seen this happen sometimes when my external hard drive is plugged in.
Disconnect everything you don't need to boot, and see if it works.

---

### Post by kspncr on 2009-01-30
Try using the SuperGrubDisk [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

It's awesome, straightforward, and has saved me more than a few times.

---

### Post by moyoy on 2009-01-30
--ignore this - I didn't read the whole post.

That initial boot screen is called the BIOS, and looks around for operating systems to use. If you don't have it set to look for CD's or the hard drive, it won't boot into an OS. Normally it shows a button to press to go into settings. See if it is set to boot to your source.

--ignore this - I didn't read the whole post.

---

### Post by stuhlmuller on 2009-01-30
When I hit F12, it does take me to the one-time boot menu but not matter which option I choose, it still takes me to the black screen with the white cursor in the corner.  I've tried the supergrub bootable disc and the supergrub bootable flashdrive as well and neither of them will work either.  Do you think it could be a hardware issue?

---

