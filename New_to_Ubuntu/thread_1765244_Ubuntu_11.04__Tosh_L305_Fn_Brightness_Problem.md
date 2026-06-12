---
title: "Ubuntu 11.04  Tosh L305 Fn Brightness Problem"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by remmian on 2011-05-22
Hello wise ones... I am a 24hr newbie to Ubuntu so please be detailed in your answer if you can help. I don't know my way around yet, or command line syntax.

Tosh L305-S5933 w/ Intel CPU and Integrated Graphics 4 Series Express Chipset
Ubuntu 11.04 64-bit installed from CD to 10GB partition (+10GB swap). 
Sole OS on computer.  

Fn F6/F7 adjusts brightness, but is not working in Ubuntu

Read about 100 posts for this problem... tried this: [http://ubuntuforums.org/showthread.php?t=1466758&highlight=fn+brightness+toshiba](http://ubuntuforums.org/showthread.php?t=1466758&highlight=fn+brightness+toshiba)
(GRUB_CMDLINE_LINUX="acpi_backlight=vendor") but it did not work. (Yes I updated grub afterward per the instructions.)

Has anyone found a solution for Toshiba users??? Thanks so much.

---

### Post by linuxguruX on 2011-05-22
> **remmian said:**
> Hello wise ones... I am a 24hr newbie to Ubuntu so please be detailed in your answer if you can help. I don't know my way around yet, or command line syntax.

Tosh L305-S5933 w/ Intel CPU and Integrated Graphics 4 Series Express Chipset
Ubuntu 11.04 64-bit installed from CD to 10GB partition (+10GB swap). 
Sole OS on computer.  

Fn F6/F7 adjusts brightness, but is not working in Ubuntu

Read about 100 posts for this problem... tried this: [http://ubuntuforums.org/showthread.php?t=1466758&highlight=fn+brightness+toshiba](http://ubuntuforums.org/showthread.php?t=1466758&highlight=fn+brightness+toshiba)
(GRUB_CMDLINE_LINUX="acpi_backlight=vendor") but it did not work. (Yes I updated grub afterward per the instructions.)

Has anyone found a solution for Toshiba users??? Thanks so much.


have you seen/tried this? 
[http://ubuntuforums.org/showthread.php?t=1492151](http://ubuntuforums.org/showthread.php?t=1492151)

---

### Post by remmian on 2011-05-22
> **linuxguruX said:**
> have you seen/tried this? 
[http://ubuntuforums.org/showthread.php?t=1492151](http://ubuntuforums.org/showthread.php?t=1492151)

Thanks, I just tried several kybds, including the Tosh Satellite, but no joy. However, I don't understand how the advanced options (level 3, as the link above refers to) relates to the Fn keys, as Fn keys are not mentioned anywhere there that I could see.

Unfortunately this computer has a very harsh screen brightness... what I really want is an applet that would allow me to adjust *contrast, gamma*, _and_ brightness. Does anything like that exist?

Thanks...!

---

### Post by remmian on 2011-05-23
Well, one thing I found that helped (for newbies like me that might read this later). In my initial post I put a link for a terminal command that returns Fn function to some laptops (but not Toshibas, sadly, or at least not mine). 

In other posts I also read about a brightness slider available via Power Button=> System Settings => Hardware => Power Management on the "On AC Power" tab. I had no such slider. 

Turns out that when you use the fix referred to in my initial post, you lose the brightness slider. Put back the line in grub like it was originally, and at least you can get the brightness slider back, which really, really helps. Not nearly as handy as having functioning Fn keys, but hey... at least my eyes aren't burning out of my head now! :D

Would still like an Fn fix if anyone has one...

---

