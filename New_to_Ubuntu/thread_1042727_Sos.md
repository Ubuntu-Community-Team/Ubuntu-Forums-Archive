---
title: "Sos"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by ReisceakaLP on 2009-01-17
I'm new to Ubuntu. Even though I haven't figured everything out I'm loving what I do know. I've read a few forums and sites but I still don't understand or the info is for another Linux version or laptop. 

The first problem is screen resolution. The largest option Ubuntu is giving me is 800x600. My laptop is an HP Pavilion dv6000. 17" widescreen, 1280x1024. I've read about opening the terminal and typing in commands but apparently I'm just not getting it.

The second problem is the NVIDIA. I go to activate it but nothing happens. I did read that after clicking "Activate" to restart  my laptop and I would see it, but it still shows it as inactive. 

Those are the only two problems I seem to have......great software! =D

---

### Post by bgerlich on 2009-01-17
Your problem may be, that you haven't updated your system's package index. You can do it using the update manager in system -> administration or by typing ```
sudo apt-get update
``` in the console.

After that you will be able to turn on the NVIDIA driver and after reboot your resolution should be normal.

This is actually a common problem, a quirk in Ubuntu that has not yet been fixed ( i think ).

---

### Post by llamakc on 2009-01-17
Under the menu path of SYSTEM > PREFERENCES > SCREEN RESOLUTION is there an option for "wide screen"?

---

### Post by albinootje on 2009-01-17
> **ReisceakaLP said:**
>  The first problem is screen resolution. The largest option Ubuntu is giving me is 800x600. My laptop is an HP Pavilion dv6000. 17" widescreen, 1280x1024.

Which Ubuntu release are you using ? 8.04.1 or 8.10 or older ?

---

### Post by albinootje on 2009-01-17
> **llamakc said:**
>  You may need to install the 915resolution package first.

That's for some Intel graphic chipsets.
[http://packages.ubuntu.com/hardy/915resolution](http://packages.ubuntu.com/hardy/915resolution)

---

### Post by llamakc on 2009-01-17
> **albinootje said:**
> That's for some Intel graphic chipsets.
[http://packages.ubuntu.com/hardy/915resolution](http://packages.ubuntu.com/hardy/915resolution)

Yes, it is. I see that there's been some bad advice already suggesting that here & elsewhere after googling. I'll edit that out. Thanks!

---

### Post by albinootje on 2009-01-17
> **ReisceakaLP said:**
> 
The first problem is screen resolution. The largest option Ubuntu is giving me is 800x600. My laptop is an HP Pavilion dv6000. 17" widescreen, 1280x1024. 

Here's someone who has some advice for perhaps the same laptop.
The author writes about several HP laptops here.
[http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops](http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops)

This is for Ubuntu 7.10, perhaps it's useful for you.
> 
After running envy on Gutsy Gibbon Tribe 6 I experienced an extended (over 1280×800) login window and and a very slow desktop with very small text in taskbar. Refresh was @51hz. The system eventually freezed.

Solution: go into recovery mode and type: sudo pico /etc/X11/xorg.conf then locate Section “Screen”
Identifier “Default Screen”
Device ….
and change values within SubSection “Display” and EndSubSection as follows:

SubSection “Display”
Virtual 1280 800
Depth 24
Modes “1280×800@60”
EndSubSection
Save with CTRL+X and Y
reboot
now everything should work and compiz should be running happily!
Also, in the graphics card driver section, add
Option “NoLogo” “true”
in order to remove the nvidia splash when X starts.
Option “OnDemandVBlankInterrupts” “true”
in order to enable power saving features.


---

### Post by albinootje on 2009-01-17
These two pages could be useful too :
[http://ubuntuforums.org/archive/index.php/t-687733.html](http://ubuntuforums.org/archive/index.php/t-687733.html)
[http://www.linuxquestions.org/questions/ubuntu-63/help-with-ubuntu-8.04-hardware-drivers-on-a-hp-pavilion-dv6000-663112/](http://www.linuxquestions.org/questions/ubuntu-63/help-with-ubuntu-8.04-hardware-drivers-on-a-hp-pavilion-dv6000-663112/)

---

### Post by ReisceakaLP on 2009-01-17
> **bgerlich said:**
> Your problem may be, that you haven't updated your system's package index. You can do it using the update manager in system -> administration or by typing ```
sudo apt-get update
``` in the console.

After that you will be able to turn on the NVIDIA driver and after reboot your resolution should be normal.

This is actually a common problem, a quirk in Ubuntu that has not yet been fixed ( i think ).

Thank you so much for the quick responses. I wasn't sure where to begin so I started with the first. The resolution and NVIDIA are both working now, thanks bgerlich and thanks again to everyone else who responded. =D

---

