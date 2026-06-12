---
title: "Complete System Meltdown"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by jaycee23 on 2010-05-28
This morning I've just had a nightmare on my laptop (specs in signature)
On it I had a very happy triple boot setup with Windows 7, Karmic and Lucid.

I booted into Lucid (I use its' grub) without any issue - checked some email on Thunderbird. Restarted to go into Karmic and I got as far as the ubuntu logo then simply got vertical strips on the display and login never appeared. I then tried to get into Lucid and the same thing happened before I got into the login screen. 

Tried **Win 7 - works absolutely fine** - not a problem. Grub obviously working fine.

Tried recovery mode in Lucid and got in via the minimal graphics option - I then uninstalled the proprietary Nvidia driver and tried to reboot and then nothing - can't even get anything in the recovery mode. I simply get vertical lines which get darker when I should get either the login in screen menu or, in recovery mode, the lines appear when I should get the various recovery options. 

Tried Karmic again - still no go thou' **I can get into tty1 via the recovery option** - so this is the only to access either of my ubuntu setups.

Out of desperation booted into my Live USB of Lucid and to my horror exactly the same thing happened, the little man and box appeared and then the cursor flashed for a few seconds and then absolutely nothing - aaarrggghhh. Just a blank screen. 

Lucid and Karmic have separate home partitions. I can't understand what has happened and what really worries me is that the live USB doesn't load up.

Everything was just peachy yesterday. I think I ran an update in Lucid this morning but surely any problem with the update wouldn't have affected my Karmic install. 

PLEASE HELP.

I'm sure there must be an issue with graphics in boot but have no idea what it could be.
:confused:
Unfortunately I'm stuck at work for the next 6 hrs so I am unable to access my laptop for now but any ideas are welcome.

---

### Post by lkraemer on 2010-05-28
I've had similar problems with a Nvidia 8200 Video card.

Here are some things I'd try to get the LiveCD working before you proceed.
There are a couple of things you can try with that LiveCD that may help.

First go here and read the information, especially about xforcevesa
at the bottom of the page.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

1. Insert the LiveCD of 10.04 and do a RESTART of the booting OS.
2. When the LiveCD starts to Spin up Hold down the Left Shift Key
until you get the Question about Splash Screen. Answer NO.
3. Hit ENTER when you see Boot:
4. As soon as the screen gets displayed about Booting hit the UP or DOWN
arrow to let you have access to the menus, before it immediately
boots.
5. Add xforcevesa cheat code and see if it will boot using vesa versus
trying to load the Nvidia drivers or whatever it tries.


Next read the posting by catharsis at:
[http://ubuntuforums.org/showthread.php?t=1491163](http://ubuntuforums.org/showthread.php?t=1491163)
It might offer some help for trying to get your system booting from the
installs on hard drive.

Once you get the system where it boots properly from LiveCD, then try
getting 10.04 booting properly from hard drive.

It sounds as if you updated, and then installed the updated video drivers
via the hardware drivers selection.  I had the same type problem,
but my video went to a fixed size.  Maybe this posting will help.
[http://ubuntuforums.org/showthread.php?t=1474284](http://ubuntuforums.org/showthread.php?t=1474284)
If you can boot with xforcevesa, and then remove the Nvidia drivers that
were installed with the update via hardware drivers, then select the
latest Nvidia drivers for your card, you should be good.  For some reason
the 8xxx cards have problems, or at least mine did and yours does also.

[http://ubuntuforums.org/showthread.php?t=990978&highlight=jockey](http://ubuntuforums.org/showthread.php?t=990978&highlight=jockey)

lk

---

### Post by jaycee23 on 2010-05-28
Tried all that - even reinstalled Lucid but still no joy - can just about get into recovery mode of Lucid and the low graphics mode allows me to get to the desktop but that's it.

Can't get into my Karmic install at all. I have changed the grub option from "quiet splash" to "nomodeset" which allows me to access recovery mode. 

Really could do with some help

:confused:

---

### Post by jaycee23 on 2010-05-28
I know if I run ```
startx
``` while in text only mode
that this causes the screen to go blank.

I suspect I need to edit the xorg file but I REALLY need some help to do this

---

### Post by jaycee23 on 2010-05-29
I have now tried manually installing nvidia's own driver from its website but still no joy!

Ideas very welcome

:(

---

### Post by mickie.kext on 2010-05-29
Does LiveCD work fine? If not, then it might be something wrong with hardware.

---

### Post by jaycee23 on 2010-05-29
Live CD works if I change "quiet splash" to "nomodeset"

Windows 7 works absolutely fine on same system

---

### Post by jaycee23 on 2010-05-29
I completely removed Lucid and was able to boot using Karmic Live CD. Reinstalled Karmic but any attempt to install a driver for Nvidia (proprietary, off Nvidia website or via Envy) results in loss of screen

Windows still works.

Is this a GPU failure issue?

---

### Post by acrazyplayer on 2010-05-29
Since typing in nomodeset works for the live cd then you should try that for the normal install. at grub press "e" to edit then type "nomodeset" after "quiet splash" and see if that works, if so then I will tell you how to make it permanent.

---

### Post by jaycee23 on 2010-05-29
> **acrazyplayer said:**
> Since typing in nomodeset works for the live cd then you should try that for the normal install. at grub press "e" to edit then type "nomodeset" after "quiet splash" and see if that works, if so then I will tell you how to make it permanent.


Done all that but no joy. Made in permanent in grub but only thing that works is running Karmic with no Nvidia drivers installed.

---

### Post by acrazyplayer on 2010-05-29
I seam to remember somewhere that someone typed in "sudo nvidia-xconfig" and that fixed there problem. So maybe it will fix yours. Nvidia drivers need to be installed obviously. After typing that I would reboot to see if it helped.

---

### Post by jaycee23 on 2010-05-29
Tried that too :(

But still very grateful for your suggestions

---

### Post by acrazyplayer on 2010-05-29
well I reread your very first post and was thinking. Can you test to make sure your gfx card is actually working in windows. Is there some game or demo you can throw at it and see how it responds. The reason I'm asking is because it does sort of seam that it could be just your gfx card. 

I'm trying to understand exactly what happened. You had the nvidia drivers installed and working fine one moment, checked email and such and rebooted to karmic then everything messed up for both distros, except windows right?

---

### Post by jaycee23 on 2010-05-29
I'll try and load up Crysis and your understanding of what happened is correct

---

### Post by jaycee23 on 2010-05-29
Just ran Crysis for 15 mins without any issues!

Really can't understand what's going on!

---

### Post by acrazyplayer on 2010-05-29
It is strange because it worked and then stopped. I could understand if it never worked in the first place but this I don't understand. To my knowledge here are the things make the screen go black. wrong refresh rate, wrong screen resolution, wrong drivers. 

have you tried commands like "sudo dpkg-reconfigure xserver-xorg"

apparently there is a Xorg.conf.failsafe in /etc/X11 but I dont know how you could go about using it. 

I dont know if this command is possible but here it is "sudo dpkg-reconfigure nvidia-settings" or maybe "sudo dpkg-reconfigure nvidia-xconfig"

---

### Post by detroit/zero on 2010-05-29
> **jaycee23 said:**
> I completely removed Lucid and was able to boot using Karmic Live CD. Reinstalled Karmic but any attempt to install a driver for Nvidia (proprietary, off Nvidia website or via Envy) results in loss of screen

Windows still works.

Is this a GPU failure issue?
No, I'd say your GPU and all your hardware are all OK. The fact that a non-Ubuntu OS on the same machine works fine is proof of that.

About all you can do is wipe both Ubuntus off your drive, reinstall, and hold off on any software updates until you can narrow down which one is causing the problem.

---

### Post by jaycee23 on 2010-06-01
Spent last 3 days trying all sorts of things. Given up on Lucid completely but can't even get Karmic to work with any form of Nvidia driver - just get a screen full of vertical stripes. Tried installing the drivers prior to any update but system still borked.

Resorted to trying OpenSuse but exactly the same issue

Will have to give up on Linux for now - at least on the laptop. Real shame.

I have NO idea what has happened. 

Meanwhile Windows 7 in its partition happily works away - in fact that's where I'm writing this from.

I no longer am looking for a solution but just an idea about what has gone wrong would be helpful.

:cry:

---

### Post by acrazyplayer on 2010-06-01
To be honest if I knew what went wrong I could help you as much as possible but I have no clue. Nothing changed in the bios did it? One easy way to know is to load up the bios and choose the setting "restore defaults" or something similar. Could be by pushing F11 or anything really but it normally says somewhere in all the bios settings. Also Nvidia released a beta driver 256 for Linux. *maybe* that could help but I kinda doubt it...I guess if nothing works you will just have to have Linux with no Nvidia drivers for now. If I find out anything I'll tell you. Good luck

---

### Post by jaycee23 on 2010-06-01
> **acrazyplayer said:**
> To be honest if I knew what went wrong I could help you as much as possible but I have no clue. Nothing changed in the bios did it? One easy way to know is to load up the bios and choose the setting "restore defaults" or something similar. Could be by pushing F11 or anything really but it normally says somewhere in all the bios settings. Also Nvidia released a beta driver 256 for Linux. *maybe* that could help but I kinda doubt it...I guess if nothing works you will just have to have Linux with no Nvidia drivers for now. If I find out anything I'll tell you. Good luck

Thanks for your time and consideration anyway

---

### Post by jaycee23 on 2010-06-04
Bump

---

### Post by ashwinhgtx on 2010-06-04
Have you tried booting an OS other than Ubuntu and openSUSE? Why not try something like Puppy Linux or DSL? Does it work with an older Ubuntu version like Hardy?

---

### Post by jaycee23 on 2010-06-05
Update on situation

Installed Karmic without any additional graphics drivers and all seems to be working well.

No luck with Lucid at all.

Will have to live without wobbly windows and 3D cube effects - rubbish!

---

### Post by wojox on 2010-06-05
Which driver did you install?

---

### Post by jaycee23 on 2010-06-05
Tried Proprietary, one from Nvidia website and even via Envy - all caused the same issue - vertical stripes at the login screen. I can hear to sound effects and can even login blindly but all I see are vertical stripes which reflect the colour of my desktop background

---

### Post by wojox on 2010-06-05
What if you create a new xorg.conf?

```
sudo nvidia xconfig
```

This will back up you old file and create a new one.

---

### Post by wojox on 2010-06-05
Maybe resetting xorg.conf to use the generic driver. In a terminal:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by jaycee23 on 2010-06-05
I have tried both those commands in the last week via various instructions on the web.

To be honest I can't tell you exactly how but I have tried them without success.

I assume I'm using the generic driver currently as after a fresh install of Karmic I have not installed any drivers for my GPU.

Some of the websites I have trawled for answers

[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

[http://www.sucka.net/2010/03/nvidia-drivers-ubuntu-10-04-lucid-lynx/](http://www.sucka.net/2010/03/nvidia-drivers-ubuntu-10-04-lucid-lynx/)

I've tried some instructions written by Philinux on this forum

The driver load fine but just cause my display to crash when I reboot

---

### Post by wojox on 2010-06-05
You said you tried openSUSE. How did you like that? I dual boot with that distro.

Have you installed the driver from the Nvidia website?

---

### Post by jaycee23 on 2010-06-05
> **wojox said:**
> You said you tried openSUSE. How did you like that? I dual boot with that distro.

To be honest I was just trying to get Linux to work and it seemed fine until the same thing happened when installing a driver for my Nvidia GPU.

What I don't understand is how it can go from working sweetly on a triple boot - Win7, Karmic and Lucid to not working at all with any Linux drivers. 

Win7 still works well and is able to handle a game like Crysis reasonably well.

---

### Post by wojox on 2010-06-05
I'm dumbfounded. Does it work in Karmic?

Did you use Gnome or KDE in opensuse?

---

### Post by jaycee23 on 2010-06-05
> **wojox said:**
> I'm dumbfounded. Does it work in Karmic?

Did you use Gnome or KDE in opensuse?

I tend to stick to gnome.

Karmic only works if there are no drivers installed

---

### Post by MooPi on 2010-06-05
I've read through this post and haven't seen a reason why you're using the Nvidia driver. If your not into the compositing effects and just need adequate drivers for video display and web browsing then the standard nouveau driver should be more than sufficient. I personally don't use the Nvidia driver any longer and don't use any fancy screen savers so the proprietary driver isn't needed.

---

### Post by jaycee23 on 2010-06-05
> **MooPi said:**
> I've read through this post and haven't seen a reason why you're using the Nvidia driver. If your not into the compositing effects and just need adequate drivers for video display and web browsing then the standard nouveau driver should be more than sufficient. I personally don't use the Nvidia driver any longer and don't use any fancy screen savers so the proprietary driver isn't needed.

I just like the eye candy :)

But as you say Karmic works just as well without.

However still completely unable to install Lucid due to blank screen issue. Live CD will load if I get change "quietsplash" to "nomodeset" but after install changing the grub settings to similar settings still fails to allow me to see the login page - can hear it perfectly!

---

