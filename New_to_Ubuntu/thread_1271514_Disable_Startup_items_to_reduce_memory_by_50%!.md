---
title: "Disable Startup items to reduce memory by 50%!"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by humphreybc on 2009-09-21
Wow I just had a bit of a trim of my session startup items and I managed to reduce my idle memory usage from about 700mb down to 313mb just by **disabling** the following in System > Preferences > Startup Applications:

AT SPI Registry Wrapper - provides support for accessibility
Bluetooth Manager - I don't use bluetooth on my laptop
Check for new Hardware Drivers - I don't plan to change my hardware on my laptop
Evolution Alarm Notifier - I don't use evolution
GNOME Login Sound
GNOME Splash Screen
Remote Desktop - Never use this
Tracker and Tracker applet - I am well organized so don't use search
Visual Assistance - Don't require this


Unfortunately my boot time from after BIOS to idle usable desktop is still 1 minute, 13 seconds.... which isn't very flash for my system specs (see signature). Anyone know of other easy ways to reduce boot time? Most of the delay seems to occur *after* I enter my username and password.

But at least by trimming my idle memory usage by over 50% I should have a bit more battery time :)

P.S Does anyone know what "Seahorse Daemon" and "User Folder Update" do?

---

### Post by kerry_s on 2009-09-21
> P.S Does anyone know what "Seahorse Daemon" and "User Folder Update" do?

keep those.

you can dump the splash screen & boot just text, it's much faster.
you can stop the fsck if you change the 1 to 0 on the end of the line.

**gksudo gedit /boot/grub/menu.lst**

remove "quiet splash" on lines 85, 135, 141

**gksudo gedit /etc/fstab**

on the very end of the uuid= line you'll see "1" change it to "0"

> 700mb down to 313mb

holly cow. :lolflag: that's pretty good.

i only have 256mb ram, i went crazy on mine. mine now idles around 60, uses less than 100.

---

### Post by humphreybc on 2009-09-21
> **kerry_s said:**
> keep those.

you can dump the splash screen & boot just text, it's much faster.
you can stop the fsck if you change the 1 to 0 on the end of the line.

**gksudo gedit /boot/grub/menu.lst**

remove "quiet splash" on lines 85, 135, 141

**gksudo gedit /etc/fstab**

on the very end of the uuid= line you'll see "1" change it to "0"



holly cow. :lolflag: that's pretty good.

i only have 256mb ram, i went crazy on mine. mine now idles around 60, uses less than 100.

I think i'll keep the splash screen... it's much prettier than lines of text :P

And also fsck is quite useful, but how do I change the number of restarts it has to have before initiating a check? At the moment it seems way too low... a check every 20 times or something, I want to change it to 50 or 100.

---

### Post by mcduck on 2009-09-21
Are you really sure you didn't have some extra program running when you checked the RAM usage the first time? Over 700MB sounds really, really high for system itself, my Ubuntu runs a bit above 300MB after boot and I haven't disabled a single thing..

What comes to disabling boot splash, the increased boot speed is mostly an illusion caused by more stuff happening on the screen. In the end it reduces boot time by 1-2 seconds max.

And then the last thing, memory usage won't affect how long your battery lasts. The amount of power used by RAM memory is very low and mostly constant regardless of what you do and how large portion of the memory is used.

---

### Post by humphreybc on 2009-09-21
> **mcduck said:**
> Are you really sure you didn't have some extra program running when you checked the RAM usage the first time? Over 700MB sounds really, really high for system itself, my Ubuntu runs a bit above 300MB after boot and I haven't disabled a single thing..


I'm pretty sure I didn't have anything else running when I first did the check.

> 
What comes to disabling boot splash, the increased boot speed is mostly an illusion caused by more stuff happening on the screen. In the end it reduces boot time by 1-2 seconds max.

Yeah I figured that would be the case, I can't imagine the boot splash taking up THAT much time.

> 
And then the last thing, memory usage won't affect how long your battery lasts. The amount of power used by RAM memory is very low and mostly constant regardless of what you do and how large portion of the memory is used.

Okay cool I'll keep that in mind. Have you got any more suggestions on how to improve boot up speed and also battery life? Does 1min 13 seconds seem quite a long boot time to you on my configuration? Or is that normal?

---

### Post by mcduck on 2009-09-21
> **humphreybc said:**
> I'm pretty sure I didn't have anything else running when I first did the check.



Yeah I figured that would be the case, I can't imagine the boot splash taking up THAT much time.



Okay cool I'll keep that in mind. Have you got any more suggestions on how to improve boot up speed and also battery life? Does 1min 13 seconds seem quite a long boot time to you on my configuration? Or is that normal?
Is that time from pressing the power button to desktop, or from Grub to GDM? In the first case it sounds quite normal with a 5400 RPM hard drive (as most of the boot process is about reading data from disk to RAM so a slow drive will easily become a bottleneck). In the latter case it's way too much, I get about 25 seconds on a Core Duo (not Core 2!) with a 5400RPM drive..

Have you tried installing Bootchart and checking the chart to see what's taking so long? If you haven't, just install the "bootchart"-package and then after a boot you'll find the chart in /var/log/bootchart.

You can also re-create the readahead list for boot, that can increase the boot sped a bit if the files used to boot have moved or changed after the install. To do that select your kernel in the Grub menu, then press "e" to edit the options and add "profle " (without quotes) to the kernel options and boot (by pressing b if you use old Grub, or Ctrl-X if you use Grub2). The boot will take quite some time as the system builds a profile of all the required files and their locations on your hard drive, just let it do it's work and when the system is running and all hard drive access has stopped reboot the machine again.


For battery life the biggest things would be display brightness and CPU power scaling. Display backlight uses a lot of power, so even dropping the brightness a couple of steps can make a great difference. CPU power scaling should work by default but you can of course check that. The services running in the background won't make a big difference when it comes to power usage, since they are idle most of the time anyway

---

### Post by humphreybc on 2009-09-21
> **mcduck said:**
> Is that time from pressing the power button to desktop, or from Grub to GDM?

It's from Grub to the usable desktop (after login). ie. Start timing *after* the BIOS screen finishes, stop timing when desktop, cairo dock, compiz is all loaded and idle. You could probably take about 5 seconds off for me typing in my username and swiping my fingerprint for login as I don't use automatic login.

> 
Have you tried installing Bootchart and checking the chart to see what's taking so long? If you haven't, just install the "bootchart"-package and then after a boot you'll find the chart in /var/log/bootchart. 

No I haven't tried that, I'll do that now and post my chart soon.

> 
You can also re-create the readahead list for boot, that can increase the boot sped a bit if the files used to boot have moved or changed after the install. To do that select your kernel in the Grub menu, then press "e" to edit the options and add "profle " (without quotes) to the kernel options and boot (by pressing b if you use old Grub, or Ctrl-X if you use Grub2). The boot will take quite some time as the system builds a profile of all the required files and their locations on your hard drive, just let it do it's work and when the system is running and all hard drive access has stopped reboot the machine again. 

I'll try this and see if it makes much difference. By the way, could you clarify on "profile" or "profle" - I presume it's just a typo on your behalf. Cheers

> 
For battery life the biggest things would be display brightness and CPU power scaling. Display backlight uses a lot of power, so even dropping the brightness a couple of steps can make a great difference. CPU power scaling should work by default but you can of course check that. The services running in the background won't make a big difference when it comes to power usage, since they are idle most of the time anyway

Okay awesome. Is there a way to disable the back light altogether like you can do on Macbooks? Or is this a hardware feature?

---

### Post by humphreybc on 2009-09-21
Okay so from power on to desktop is 1min, 22 seconds.

Attached is my bootchart. I'm not sure how to read this, so if you could offer advice that'd be great.

EDIT: It says the boot time was 24 seconds, but that's not right... it definitely takes longer than that. Is the 24 seconds just measuring the time from GRUB to the **login screen?** Because after I login, it takes a good 20 seconds or more to actually load my wallpaper and panel etc etc

Cheers

---

### Post by t0p on 2009-09-21
> **humphreybc said:**
> Okay so from power on to desktop is 1min, 22 seconds

Okay I'm confused.  Earlier you said it was 1 min 22 secs from grub to gdm.

I don't think that's a bad boot time from power on to desktop.  Though other folk may have different ideas...

---

### Post by humphreybc on 2009-09-21
Sorry, i'll clarify:

1 min 22 seconds **including** the BIOS.

1 min 13 seconds **not** including the BIOS (ie, from GRUB onwards).

In both times, the stopwatch was stopped when the following were all satisfied:

Wallpaper loaded
Cairo Dock loaded
Compiz loaded
Panel loaded with all applets running

---

### Post by mcduck on 2009-09-21
I'd say your boot time is actually pretty normal now. 24 seconds from Grub to GDM (as the bootchart reports) is quite fine with a slow hard drive. The boot process doesn't seem to stop at any time (so no stalling processes or other problems) and most of the time is spent by reading data from your hard drive.

There's quite a lot of stuff starting, but disabling anything would most likely only give you a second or two less boot time and have no noticeable effect on battery life or actual performance when the system is running so I wouldn't bother.

I'd say that disabling backlight completely is a hardware feature (my iMac doesn't do that, laptop does with it's own keyboard button but the screen is completely unusable without backlight, even in strong sunlight). But just drop it as low as you can without sacrificing usability and you can easily gain 20-30 minutes of extra battery life. Actually I get that just by dropping from 100% to 80%..

(and yes, it was supposed to be "profile" :D)

---

### Post by humphreybc on 2009-09-21
Okay so 24 seconds from GRUB to GDM is good, but you can't exactly use the computer at GDM until you login... and it's from the login onwards that seems unusually slow. Advice?

Here's a wiki entry on this exact issue: [https://wiki.ubuntu.com/BetterLoginSpeed](https://wiki.ubuntu.com/BetterLoginSpeed)


I think it's silly trying to reduce the boot time to under 10 seconds if the login time is still greater than 30 seconds!

---

### Post by apocalypse80 on 2009-09-21
Edit /boot/grub/menu.lst and add the parameter bootchart=nostop (after ro quiet splash).
That way bootchart will not stop on it's own.

After the system has fully loaded, run "sudo /etc/init.d/stop-bootchart start" to stop bootchart.
That way you'll get a log of the entire boot process.

Oh and remember to go back to menu.lst and remove the bootchart parameter after you're done.

Alternative suggestion ; create a new user and try logging in as that one.
It should be faster and it will give you an idea of how much those applets cost you.

---

### Post by humphreybc on 2009-09-21
I just registered an Ubuntu blueprint for faster login speed in 10.04:

[https://blueprints.launchpad.net/ubuntu/+spec/ubuntu-login-speed](https://blueprints.launchpad.net/ubuntu/+spec/ubuntu-login-speed)

---

