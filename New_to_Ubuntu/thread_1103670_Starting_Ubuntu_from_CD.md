---
title: "Starting Ubuntu from CD"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by stymie on 2009-03-22
I have the Ubuntu 8.10 Desktop Edition CD and want to browse it before installing and deleting my Windows Vista software.  I have put the CD in the drive and rebooted but nothing happens.  It doesn't launch.  Is there a way to launch it by going into the CD drive and picking one of the commands the CD shows.  I'm not good with changing commands or altering my BIOS and don't want to if I don't have to and can run the program from the CD itself.

Thanks for any help...

---

### Post by bumanie on 2009-03-22
You need to enter your bios settings and have the computer set to boot from cd-rom as th efirst boot device and have the ubuntu cd in the drive when you boot. Each system is different, but on the POST screen you should see an instruction that tells you to push esc or F12 or delete to enter setup. Setup is usually your bios settings for the motherboard. Also, ensure you have burned the cd as an image not as a data cd - .iso files must be burned as an image or else they won't work.

---

### Post by abn91c on 2009-03-22
what brand PC? you will need to boot from the cd, if using a Dell press f12 at  the Dell logo, otherwise go into the bios and change the boot sequence to cdrom, then HDD

---

### Post by stymie on 2009-03-22
> **abn91c said:**
> what brand PC? you will need to boot from the cd, if using a Dell press f12 at  the Dell logo, otherwise go into the bios and change the boot sequence to cdrom, then HDD
It is a custom built PC with an ASUS motherboard.

---

### Post by stymie on 2009-03-22
> **bumanie said:**
> You need to enter your bios settings and have the computer set to boot from cd-rom as th efirst boot device and have the ubuntu cd in the drive when you boot. Each system is different, but on the POST screen you should see an instruction that tells you to push esc or F12 or delete to enter setup. Setup is usually your bios settings for the motherboard. Also, ensure you have burned the cd as an image not as a data cd - .iso files must be burned as an image or else they won't work.
The CD is directly from UBUNTU.  It is not one that I burned.

---

### Post by my window broke on 2009-03-22
when you boot up, it should tell you the button to press at either the top right of the screen or top left (sometimes over the loading bar, but I haven't really seen that alot).

---

### Post by Bartender on 2009-03-22
BIOS access for most ASUS boards is Del key while it's first booting up.  You shouldn't be intimidated by BIOS - it's pretty easy once you've poked around in there a few times and it's a skill you'll almost certainly need.  Even if it's only to change the boot priority.
Your mouse won't work in BIOS, so look for the quick guide at the bottom of the screen to tell you how to navigate.  Look for Boot Priority, Enter, then move the optical drive to the #1 position.  Enter, then there's a keystroke to save the setting and leave BIOS.  PC will reboot and you should see the optical drive LED come on as the PC looks to it first for a bootable device.

---

