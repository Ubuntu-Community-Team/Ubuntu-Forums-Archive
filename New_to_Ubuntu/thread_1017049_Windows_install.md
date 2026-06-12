---
title: "Windows install"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by Exit18 on 2008-12-20
I'm trying to partition Windows XP and Ubuntu on my computer. I have an official CD, but it won't install. The menu pops up just fine, but when I click "install" It comes up for a second, then freezes. Any suggestions?

---

### Post by Exit18 on 2008-12-20
I'm trying to partition Windows XP and Ubuntu (Hardy version) on my computer, but I'm running into problems. I'm mainly doing this for gaming, so stuff like VMware is of no good to me. Anyway, I put the CD in and the install screen comes up just fine. However, when I hit "install Windows XP it freezes up after a second or two." Any suggestions?

---

### Post by will1911a1 on 2008-12-20
> **Exit18 said:**
> I'm trying to partition Windows XP and Ubuntu (Hardy version) on my computer, but I'm running into problems. I'm mainly doing this for gaming, so stuff like VMware is of no good to me. Anyway, I put the CD in and the install screen comes up just fine. However, when I hit "install Windows XP it freezes up after a second or two." Any suggestions?

Are you booting from the WinXP disc or what?

---

### Post by overdrank on 2008-12-20
Please do not create multiple threads on the same issue. Threads merged. :)

---

### Post by Exit18 on 2008-12-20
I tried to boot off the disc, but it won't for some reason. I'm trying to install it from inside Ubuntu, and as I said before, the setup worked until the moment I actually tried to install.

---

### Post by Exit18 on 2008-12-20
> **overdrank said:**
> Please do not create multiple threads on the same issue. Threads merged. :)

Sorry about that, that first thread was a mistake. I tried to pm a mod to delete it, but I guess they logged off or something. =P

---

### Post by will1911a1 on 2008-12-20
> **Exit18 said:**
> I tried to boot off the disc, but it won't for some reason. I'm trying to install it from inside Ubuntu, and as I said before, the setup worked until the moment I actually tried to install.

What happens when you try to boot from the WinXP disc?

---

### Post by eagle416 on 2008-12-20
So let's get this straight - you're in Ubuntu, booted up, and you put the Windows XP disc in your computer, and a window came up?

---

### Post by kansasnoob on 2008-12-20
So, do you have XP installed and now trying to install Ubuntu or Ubuntu installed and now trying to install XP?

I suspect the latter:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by Exit18 on 2008-12-20
> **eagle416 said:**
> So let's get this straight - you're in Ubuntu, booted up, and you put the Windows XP disc in your computer, and a window came up?

Yes, exactly.

> **will1911a1 said:**
> What happens when you try to boot from the WinXP disc?
Nothing.

---

### Post by will1911a1 on 2008-12-20
> **Exit18 said:**
> 
Nothing.

So the computer just hangs or what?  Does it eventually boot into Ubuntu?

Are you sure you have the boot order set to look at your CD drive first?

---

### Post by eagle416 on 2008-12-20
Okay, so I have the feeling you tried to install Windows XP onto WINE.

Turn off your computer.
Turn on your computer. When the manufactuerer logo pops up, hit the setup or boot order button (usually F12). - this goes into BIOS.
Set CD Priority to 1 (or higher than your Hard Drive). Now your computer will boot from CD.

Now restart the computer WITH the XP cd in.

---

### Post by eagle416 on 2008-12-20
Okay, so I have the feeling you tried to install Windows XP onto WINE.

Turn off your computer.
Turn on your computer. When the manufactuerer logo pops up, hit the setup or boot order button (usually F12). - this goes into BIOS.
Set CD Priority to 1 (or higher than your Hard Drive). Now your computer will boot from CD.

Now restart the computer WITH the XP cd in.

---

### Post by nhasian on 2008-12-20
you need to change your bios settings to allow you to boot off a CD.  reboot your PC, then hit the key to enter the BIOS setup before the OS starts to load.  depending on your computer the key may be DEL, F2, F10, etc.

Once in the BIOS there will be a lot of submenus.  in one of them it will have a list of devices to boot off of something like:

1. HDD0
2. CD/DVD
3. Network
4. USB
5. Floppy

you will need need to make the CD/DVD device boot before the HDD or Hard Disk drive.  then save and exit and you will be able to boot off a CD.

---

### Post by kansasnoob on 2008-12-20
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by SunnyRabbiera on 2008-12-20
also if you are starting fresh install XP first.
XP is a space hod and would want the whole drive to itself.

---

### Post by eagle416 on 2008-12-20
> **SunnyRabbiera said:**
> also if you are starting fresh install XP first.
XP is a space hod and would want the whole drive to itself.

And it'll also override GRUB.

---

