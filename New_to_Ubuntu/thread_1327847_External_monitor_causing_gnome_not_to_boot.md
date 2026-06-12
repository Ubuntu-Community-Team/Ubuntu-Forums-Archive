---
title: "External monitor causing gnome not to boot"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by NittanyBobcat on 2009-11-15
Hello all - 

Thanks in advance for the help - I know y'all are volunteering to help newbies like me out. Very much appreciated.

I'm new to Ubuntu/linux - lots of experience on Windows (up to XP). 

My problem is when I attach an external monitor to my Dell 710m laptop. I tried Ubuntu out in Wubi first, and it worked without a hitch in Wubi (although I think that was 9.04). I've now installed 9.10 (dual boot with XP), and while Ubuntu recognizes my external monitor (under Display Preferences), but the external monitor is turned off in the preferences. When I activate it, I get a message about virtual settings, and it tells me to log off. 

When I log out, the system goes to a black screen with a blinking cursor in the upper left. It then begins to flash the command line login prompt very quickly - I'm not able to log in - it just keeps flashing on and off until I can power down. Upon reboot, the same thing happens. 

When I choose recovery mode (I think that's what it's called) from grub, I can get to a command line login, and doing a ls command shows that everything is still there - it's just the gui that won't boot. To get the GUI back, I had to reinstall Ubuntu from the ISO. Tried the external monitor again, with the resolution of 640X400 - it showed up on the external monitor, but only the corner of the screen - like it's zoomed in. I changed the resolution to something higher - and yes, had to end up reinstalling again. 

Any help you can give would be appreciated.

---

### Post by Bölvaður on 2009-11-15
to avoid having to reinstall take backup of your xorg.conf

I am not going to let you copy and paste commands mindlessly, as then you wouldnt learn ;)

press Alt+F2
```
gksu nautilus
```
and backup /etc/X11/xorg.conf by copying and pasting + renaming.
I know you can do that in less than 10 seconds in the terminal but I am evil.


Now in the future if you lose gui you just pick recovery from grub and replace the current xorg.conf with the backup one with something like
```
mv /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```
press ESC or type exit and choose to log in normally.


It may be good to know if you have the correct driver installed. I trust you to know if you installed a driver or not and what graphic card you have. And then post it here.

Turn the computer on with the vga cable already in and see what happens.

(I have forgotten what my solution to your problem is.. I swear I knew it few minutes ago)

---

### Post by NittanyBobcat on 2009-11-16
Hi Bolvadur - thanks for the prompt reply! 

I hadn't downloaded any proprietary drivers - and I have the Intel video card (chipset). 

Strangely enough - the one thing I hadn't tried was plugging in the cable before booting up - I had done it from hibernation, but that didn't work - the reboot did it. And it got my creative zen working at the same time.

Sometimes the simplest solutions are best!

Thanks again!

---

