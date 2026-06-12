---
title: "Ubuntu not booting after upgrade on ASUS T-91MT"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by chidat on 2011-05-01
Hi,

I just upgraded to Ubuntu 11.04 on my ASUS T-91MT netbook, but during the final "restart the computer" step, Ubuntu wouldn't boot up. When I select it in the GRUB menu (I'm dual-booting), all I get is a blank screen with a blinking cursor. I thought it might be configuring things, but after a couple of hours, I concluded that it was probably not. I was able to upgrade successfully on my laptop, with no such problems. It booted up right away (although slower than 10.10 did..)
I can't boot it off a live CD, because I don't have an external CD/DVD drive, but I *am* able to run it in "failsafe graphic mode" by booting into recovery mode.
Running "previous Linux versions" does not work either, since I just get the same blank screen with a blinking cursor.
Any help I could get with this would be greatly appreciated!
Thank you!

---

### Post by Rubi1200 on 2011-05-01
Sounds like it might be a graphics issue. What graphics card do you have installed and how much RAM?

---

### Post by chidat on 2011-05-02
The T91MT has an Intel GMA500 graphics card with 1GB RAM.

---

### Post by Rubi1200 on 2011-05-02
According to this your card may not have the required support:
[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements)

Can you boot into the Classic desktop?

---

### Post by chidat on 2011-05-02
Thanks for your reply!

No, I cannot, unless I'm booting it off the fail-safe graphics mode in recovery mode. I know that I do not have the hardware requirements for Unity, because it says so when I try to boot into Ubuntu from the fail-safe graphics mode. As soon as I hit enter in GRUB, I just get a blank screen except for the blinking cursor. I *would* just use Ubuntu Classic, only I can't even get to the login screen.

---

### Post by azelter on 2011-05-05
In grub, hit the e key to edit the boot line and remove the quite/splash options. Then boot (b key) your computer again [see this page for more info [http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html]](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html]).
This will cause your computer to display much more information when booting.
Let us know what it says ...

---

### Post by chidat on 2011-05-07
After removing "quiet" and "splash" in the boot line and booting, I get:

"Booting a command list

alloc magic is broken at 0x3f3b4590
Aborted. Press any key to exit."

I hope is what you are looking for.

Thank you!

----------Edit-------------
When I tried this again and left the extra space before "quiet", when I booted Ubuntu (by pressing F10), I just got the same blank screen again..

---

### Post by azelter on 2011-05-08
Can you paste in the whole line (the one that you were editing) that is being passed at boot time?

---

### Post by chidat on 2011-05-09
> **azelter said:**
> Can you paste in the whole line (the one that you were editing) that is being passed at boot time?

linux /boot/vmlinuz-2.6.38-8-generic root=UUID=... ro a\cpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=\1024x600-24,mtrr=3,scroll=ywrap pci=nocrs mem=896mb  quiet splash vt.handoff=7

---

### Post by azelter on 2011-05-09
Try looking at the line you just posted and compare it to the failsafe boot line. You will see several differences. Try making the non-failsafe line look more like the failsafe line. You can google any parameters you do not understand. This may help you to get the non-failsafe mode to boot.

---

### Post by chidat on 2011-05-10
the recovery mode boot parameters are:

linux /boot/vmlinuz-2.6.38-8-generic root=UUID=... ro **single** acpi_osi=Linux  acpi_backlight=vendor acpi_skip_timer nomodeset  video=uvesafb:mode_option=1024x600-24,mtrr=3,scroll=ywrap pci=nocrs  mem=896mb

the only difference is the word "single", other than the omission of "quiet splash vt.handoff=7", but changing the non-recovery mode one to look like this one either makes it boot into recovery mode (if I change it to look completely identical), or it does not work at all.. what's going on??? :confused:

thanks for all your help so far!

---

