---
title: "Screen Resolution Problems"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by pseudosmart on 2010-08-25
I have a Sony Vaio laptop with a 17" widescreen LCD display. I have the largest screen resolution selected, but the far right and the bottom of the screen are chopped off, so I can't see the panel or taskbar at the bottom of the screen. Does anyone know how I can fix this? I am brand new at using Linux, so if it involves using the terminal, I would need step by step instructions. I apologize for my ignorance, but would appreciate any help anyone has to offer. I'm excited to get the screen resolution fixed and start using Ubuntu!

---

### Post by snip3r8 on 2010-08-25
First off what distribution are you using?

Second,if the laptop has an Nvidia or ATI graphics card,Installing a proprietary driver may solve the problem

---

### Post by leprkhn on 2010-08-25
You want to open your Monitor Preferences.
System > Preferences > Monitors

Choose one of the widescreen (16:10) resolutions in the Resolution dropdown menu to the right. I'd start with the lowest one ( 1152x648 ), and work your way up to the one that feels right to your eyes. My guess on a 17" monitor is that your final resolution will be 1440x900.

I hope this helps.

---

### Post by pseudosmart on 2010-08-25
I am using 10.04.1. Do you know how I would install the proprietary driver? Thanks in advance for your help.

---

### Post by pseudosmart on 2010-08-25
**Re: Screen Resolution Problems**
 		You want to open your Monitor Preferences.
System > Preferences > Monitors

Choose one of the widescreen (16:10) resolutions in the Resolution  dropdown menu to the right. I'd start with the lowest one ( 1152x648 ),  and work your way up to the one that feels right to your eyes. My guess  on a 17" monitor is that your final resolution will be 1440x900.

I hope this helps.


Thanks for the suggestion, but I have tried every screen resolution available in System>Preferences>Monitors. The largest resolution looks best, but it just cuts off the right and the bottom of the screen. Do I have to create a custom screen resolution some how?

---

### Post by snip3r8 on 2010-08-25
It depends on your graphics card

if its nvidia then go here:

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

if you need help with that then go to:

[URL="http://ubuntuforums.org/showthread.php?t=990978&highlight=install+nvidia"]http://ubuntuforums.org/showthread.php?t=990978&highlight=install+nvidia
[/URL]
Im not sure about what you would do with ATI ,if you have trouble search the forums, but the download is here:

[http://support.amd.com/us/gpudownload/fire/Pages/fire_linux.aspx](http://support.amd.com/us/gpudownload/fire/Pages/fire_linux.aspx)

---

### Post by leprkhn on 2010-08-25
First find out what kind of video hardware you have.
```
sudo lspci | grep -i VGA
```

If you install the proprietary ATI or NVIDIA driver, don't forget to install build essential.
```
sudo apt-get install build-essential
```

Things may have changed since the last time in did this, but I think it goes something like this:

Stop GDM (this will drop you to a terminal)
```
sudo /etc/gdm stop
```
Navigate to the directory where you downloaded the drivers.
```
cd /path/to/driver/package
```
Run package
```
sudo sh name.of.driver.package
```
If this doesn't work, make sure that the file is executable.
```
chmod +x name.of.driver.package
```
Follow the instructions provided by the installer once you get it to run. Default options should work.

This being said, you may also find the drivers you need by going to Administration > Hardware Drivers and letting Ubuntu do all the work for you.

---

### Post by leprkhn on 2010-08-25
> **leprkhn said:**
> First find out what kind of video hardware you have.
```
sudo lspci | grep -i VGA
```

If you install the proprietary ATI or NVIDIA driver, don't forget to install build essential.
```
sudo apt-get install build-essential
```

Things may have changed since the last time in did this, but I think it goes something like this:

Stop GDM (this will drop you to a terminal)
```
sudo /etc/gdm stop
```
Navigate to the directory where you downloaded the drivers.
```
cd /path/to/driver/package
```
Run package
```
sudo sh name.of.driver.package
```
If this doesn't work, make sure that the file is executable.
```
chmod +x name.of.driver.package
```
Follow the instructions provided by the installer once you get it to run. Default options should work.

This being said, you may also find the drivers you need by going to Administration > Hardware Drivers and letting Ubuntu do all the work for you.

Sorry...
If you're installing the proprietary package you'll probably want to go ahead and start GDM again after installation, huh?
```
sudo /etc/init.d/gdm start
```

---

### Post by pseudosmart on 2010-08-25
Well, I was successfully able to install the correct proprietary driver I think. But the highest resolution available now is 2048:1536 (4:3), and I still can see the bottom panel or taskbar. Any further suggestions? Thank you again for your help so far.

---

### Post by formaldehyde_spoon on 2010-08-25
When I want install proprietry display drivers I just go to System > Admin > HardwareDrivers  and then just click 'yes, install drivers'.

OP, tell us what happens when you select different resolutions in System > Preferences > Monitor Settings/Resolution

---

### Post by meem1029 on 2010-08-25
As a comment, I am also on a 17" Sony so assuming that it is the Vaio EC and was purchased recently, it probably has a 1600x900 resolution.

---

### Post by pseudosmart on 2010-08-26
> **meem1029 said:**
> As a comment, I am also on a 17" Sony so assuming that it is the Vaio EC and was purchased recently, it probably has a 1600x900 resolution.
Do you know how I could change my resolution to 1600x900? That is not one of the screen resolutions available in System>Preferences>Monitors for me?

---

### Post by Verbeck on 2010-08-26
Run this in the terminal
```
sudo gedit /etc/X11/xorg.conf
```
look for the following or something similar
```
 Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1440x900 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```
Edit 1440x900 to the resolution you need and logout to restart X

Hope this helps :)

---

### Post by Daniel0108 on 2010-08-26
You could also go to: System->Administration->Hardware drivers
And install all the drivers ;)
There should be a driver for your graphic card, or for your screen.. Install the drivers, restart your computer and then change your screen resolution..
Hope this helps,
Daniel

---

### Post by pseudosmart on 2010-08-26
> **Verbeck said:**
> Run this in the terminal
```
sudo gedit /etc/X11/xorg.conf
```look for the following or something similar
```
 Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1440x900 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```Edit 1440x900 to the resolution you need and logout to restart X

Hope this helps :)

Thanks for the suggestion. I tried cvt and xrandr to try some different resolutions out without making permanent changes, and I can't find one that works. Any ideas for what resolution I should use for sony vaio 16" widescreen? No matter what resolution I try, the bottom and right side of the screen are cut off.

---

### Post by Daniel0108 on 2010-08-26
Try my suggestion, and see if your graphic card configures the resolution ;)
Yours,
Daniel

---

### Post by pseudosmart on 2010-08-26
> **Daniel0108 said:**
> Try my suggestion, and see if your graphic card configures the resolution ;)
Yours,
Daniel

I tried that, but it didn't work. I have attached a screenshot of what my screen looks like, if it helps. It's sill missing the far right and bottom of the screen.

---

### Post by Daniel0108 on 2010-08-26
hmm..
have you tried to change the monitor settings again AFTER installing the graphic card driver?
Yours,
Daniel

---

### Post by pseudosmart on 2010-08-26
> **Daniel0108 said:**
> hmm..
have you tried to change the monitor settings again AFTER installing the graphic card driver?
Yours,
Daniel

Yeah, I have, and it still didn't work. I found another thread about problems with widescreen displays, which I have. That thread suggested running sudo apt-get install 855resolution, and rebooting to resolve the issues. Do you think that is something that might work?

---

### Post by Daniel0108 on 2010-08-26
hi
I have a widescreen too...
I installed the graphic driver and it worked..
but there was an update named screen-resolution-extra... Maybe this package help you...
just type sudo apt-get install screen-resolution-extra
if it don't work.. try this sudo apt-get install 855resolution... but I dunno this package ;)
Yours,
Daniel

---

### Post by pseudosmart on 2010-08-26
Does it make a difference that my xorg.conf file is blank? I have read several posts on different forums that state this file is largely blank in new versions, but I just thought I'd ask.

---

### Post by pseudosmart on 2010-08-26
I thought I would add that the problem with my screen cutting off at the right and bottom is not limited to Ubuntu. I tried to run fedora and Suse, and the had the same problems.

---

### Post by Daniel0108 on 2010-08-27
Oh... Thats bad.. 
If your file is blank, have you tried to insert the code into the file?
That worked for me on my other computer with Lucid Lynx 10.04 (now have 10.04.1 ;) )
PS: There I couldn't set the screen resolution on Monitors (I only could choose 400x800 and nothing else) :P
Yours,
Daniel

---

### Post by pseudosmart on 2010-08-31
I FINALLY figured it out! I had to disable the nouveaux (sp?) open source driver for nvidia cards, THEN install the proprietary driver for my card, THEN install nvidia-settings, THEN reboot, and use nvidia-settings to adjust my screen resolution. Thanks everybody for your help. I'm so relieved I finally found a solution.

---

### Post by Daniel0108 on 2010-09-01
> **pseudosmart said:**
> I FINALLY figured it out! I had to disable the nouveaux (sp?) open source driver for nvidia cards, THEN install the proprietary driver for my card, THEN install nvidia-settings, THEN reboot, and use nvidia-settings to adjust my screen resolution. Thanks everybody for your help. I'm so relieved I finally found a solution.

Fine, THEN please click on Thread options>Mark this thread as sloved :)
Yours,
Daniel

---

