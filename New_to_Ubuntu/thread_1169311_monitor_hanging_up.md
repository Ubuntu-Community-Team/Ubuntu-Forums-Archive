---
title: "monitor hanging up"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by PFN on 2009-05-25
I am new to ubuntu and linux.
I installed ubuntu 9.04_i386 a few days before and dual booting with windows XP. I am facing a problem with ubuntu is that my monitor hangs after every 2 minutes while iam playing any video, or using web browser or downloading anything(the status bar). Sound continue playing.On moving mouse or press any keyboard button it resume playing.I checked screensaver settings and it is disabled.I never face this problem in windows.This may be a silly mistake of mine, but Please consider as a newbie and help me.
Details:
Intel Pentium Dual Core CPU 1.80GHz,
Intel 82945 G/GZ Integrated graphics Controller,
2GB DDR2 RAM

---

### Post by Bölvaður on 2009-05-25
try add xforcevesa to your boot parameters.

you do that by (from turning on the computer)

press ESC when you are asked to get into the GRUB (bootloader)
press E to edit the boot parameters
add "xforcevesa" at the end of the line
Press ESC to stop editing
press B to boot with these temperate settings (they will change back on next boot).


Do you have same problem now?

If yes, then you might want to look at your ram, in grub find memtest and press enter on it to use it. then run the memtest few times, for about half an hour to an hour depending on how big your ram is.

If you did not have problem any more then you will need to change xorg.conf to VESA
there are many detailed threads about it on this forum about how to switch to a different driver, just by changing that config file xorg.conf

---

### Post by donato roque on 2009-05-25
Hi
You should check your power management preferences.  Go to System>Power Management.  then use the sliders to set your preferences.
If you watch a lot of video clips set display to sleep appropriately.

Good luck!

---

### Post by PFN on 2009-05-25
Thanks  Bölvaður and Donato Roque for your response.
I done reboot with the line "xforcevesa " added to boot parameters, but the problem remains. I also confirmed the sliders in the power management settings are set to Never.
Now what to do?

---

### Post by Bölvaður on 2009-05-25
Intel 82945 G/GZ Integrated graphics Controller



oh... I didnt see that before.
Try ubuntu 8.10 live cd out. there is a problem with intel integrated graphics card at the moment in 9.04, but there are howtos on this forum on how to fix that.

---

### Post by PFN on 2009-05-26
Thanks [Bölvaður]("http://ubuntuforums.org/member.php?u=338535").
I already searched the forum and found a thread _**'**_**HOWTO: Jaunty Intel Graphics Performance Guide'** at[B][URL="http://ubuntuforums.org/showthread.php?t=1130582&page=59"] http://ubuntuforums.org/showthread.php?t=1130582&page=59

[/URL][/B][Now I am going to try that.Thanks for your guidence]("http://ubuntuforums.org/showthread.php?t=1130582&page=59")

---

