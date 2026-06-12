---
title: "can't change the resolution of the screen"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by thailand on 2011-06-22
I tried to change the size of the screen via System/Preferences/Monitors, but the Resolution can't not change.
What should I do?
My version is Ubuntu 11.04
Thank you in advance

---

### Post by terrykiwi83 on 2011-06-22
first we need specs, what type of video card do you have?

---

### Post by thailand on 2011-06-22
Intel(r)845G/845GL/845GE/845GEV Graphics

---

### Post by terrykiwi83 on 2011-06-22
Have you checked Additional Drivers to see if you can install any restricted drivers?

here are some guides from another post
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

---

### Post by wildmanne39 on 2011-06-22
> **thailand said:**
> Intel(r)845G/845GL/845GE/845GEV Graphics
Hi, intel is supported in the kernel so you do not need a updated driver.If in doubt that module loaded correctly type this into a terminal
```
sudo lspci -k
```
post the outcome  here by clicking on new reply and click # and paste the information between the brackets.
also you can manually adjust them by using the directions from these two links, only one method is needed just pick the one easiest for you to do.
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)
make sure you do not set a range higher then the resolution of your monitor or you could damage it.

---

### Post by terrykiwi83 on 2011-06-22
cheers again wildmanne39 :D

---

### Post by thailand on 2011-06-22
This is the outcome
```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
    Subsystem: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
    Subsystem: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
    Kernel driver in use: i915
    Kernel modules: intelfb, i915
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
    Subsystem: Intel Corporation Latitude X300
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
    Subsystem: Intel Corporation Latitude X300
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
    Subsystem: Intel Corporation Latitude X300
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
    Subsystem: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
    Kernel modules: shpchp
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
    Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
    Subsystem: Intel Corporation Device 24c2
    Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
    Subsystem: Intel Corporation Device 24c2
    Kernel modules: i2c-i801
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
    Subsystem: Device 414c:4730
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0
01:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

```

---

### Post by wildmanne39 on 2011-06-22
Hi, yes they are loaded and working, you will have to change the resolution using one of the two links I gave you in my last post.

---

### Post by thailand on 2011-06-22
I typed the command [COLOR=Red]xrandr[/COLOR], but it failed. Here is the outcome
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1600 x 1200, current 1600 x 1200, maximum 1600 x 1200
default connected 1600x1200+0+0 0mm x 0mm
   1600x1200       0.0*
```

---

### Post by wildmanne39 on 2011-06-22
> **thailand said:**
> I typed the command [COLOR=Red]xrandr[/COLOR], but it failed. Here is the outcome
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1600 x 1200, current 1600 x 1200, maximum 1600 x 1200
default connected 1600x1200+0+0 0mm x 0mm
   1600x1200       0.0*
```Hi, the command did not fail that is what is in the file, that means it is not recognizing your monitor, and to edit it you will need to follow the instructions on that link.

---

### Post by thailand on 2011-06-22
I entered the following commands, but it failed too.
First command: [COLOR=Red]cvt 1024 768[/COLOR]
The outcome is
```
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
```
Second command: [COLOR=Red]xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync[/COLOR]
The outcome is
```
xrandr: Failed to get size of gamma for output default
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  19
  Current serial number in output stream:  19
```
The third command: [COLOR=Red]xrandr --addmode S-video 1024x768[/COLOR]
The outcome is
```
xrandr: Failed to get size of gamma for output default
xrandr: cannot find output "S-video"
```

---

### Post by wildmanne39 on 2011-06-22
Hi, use the other link I gave you in my other post and see if you can do it by editing the xorg config file.

---

### Post by thailand on 2011-06-23
I typed this code in /etc/X11/xorg.conf, and it works.
[COLOR=Red]Thank wildmanne39 very much![/COLOR]
```
Section "Device" 
        Identifier      "Intel 945G " 
        Driver         "intel" 
 
        # Using the name of the output defined by the video driver plus the identifier of a 
        #     monitor section, one associates a monitor section with an output by adding an 
        #     option to the Device section in the following format: 
        #     Option "Monitor-outputname" "monitor ID" 
 
        Option          "monitor-VGA" "foo" 
        #Option         "monitor-TMDS-1" "dvi" 
EndSection 
 
Section "Monitor" 
        Identifier      "foo" 
        # specifies a mode to be marked as the preferred initial mode of the monitor 
        # Option "PreferredMode"  "800x600" 
        # This optional entry specifies the position of the monitor within the X screen. 
        #Option        "Position" "1024 0" 
        #This optional entry specifies that the monitor should be ignored 
        #     entirely, and not reported through RandR.  This is useful if the 
        #     hardware reports  the  presence  of  outputs  that do not exist. 
        #Option "Ignore"  "true" 
EndSection 
 
Section "Screen" 
        Identifier      "Default Screen" 
        Device        "Intel Corporation 945G Integrated Graphics Controller" 
        Monitor       "foo" 
        DefaultDepth  24 
        SubSection "Display" 
                Depth          24 
                Modes         "1280x1024"  "1024x768"   "640x480" 
        EndSubSection 
EndSection
```

---

### Post by wildmanne39 on 2011-06-23
> **thailand said:**
> I typed this code in /etc/X11/xorg.conf, and it works.
[COLOR=Red]Thank wildmanne39 very much![/COLOR]
```
Section "Device" 
        Identifier      "Intel 945G " 
        Driver         "intel" 
 
        # Using the name of the output defined by the video driver plus the identifier of a 
        #     monitor section, one associates a monitor section with an output by adding an 
        #     option to the Device section in the following format: 
        #     Option "Monitor-outputname" "monitor ID" 
 
        Option          "monitor-VGA" "foo" 
        #Option         "monitor-TMDS-1" "dvi" 
EndSection 
 
Section "Monitor" 
        Identifier      "foo" 
        # specifies a mode to be marked as the preferred initial mode of the monitor 
        # Option "PreferredMode"  "800x600" 
        # This optional entry specifies the position of the monitor within the X screen. 
        #Option        "Position" "1024 0" 
        #This optional entry specifies that the monitor should be ignored 
        #     entirely, and not reported through RandR.  This is useful if the 
        #     hardware reports  the  presence  of  outputs  that do not exist. 
        #Option "Ignore"  "true" 
EndSection 
 
Section "Screen" 
        Identifier      "Default Screen" 
        Device        "Intel Corporation 945G Integrated Graphics Controller" 
        Monitor       "foo" 
        DefaultDepth  24 
        SubSection "Display" 
                Depth          24 
                Modes         "1280x1024"  "1024x768"   "640x480" 
        EndSubSection 
EndSection
```
Hi, your welcome, would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by thailand on 2011-06-23
> Hi, your welcome, would you please go to the top of the page and mark  this thread solved be clicking on thread tools. Thank you so much.
I've done it. I wanted to do so when I posted the last post, but I did not know how to.

I've abandoned the change of xorg.conf, because it took some other problems. I guess the code is partly wrong. It's too hard for me to write the correct code. Sorry for that my English and Ubuntu are both poor.
Thank you again

---

### Post by thailandb on 2011-08-12
I tried to modify the file ~/.config/monitors.xml, and it works!
[COLOR="Red"]Very good! So simple![/COLOR]

---

