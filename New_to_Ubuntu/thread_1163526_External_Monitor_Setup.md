---
title: "External Monitor Setup"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by Glenn8Friedrice on 2009-05-18
Hello, I'm a Ubuntu newbie.

I apologize in advance if this subject has been discussed at length prior, but I performed a search and couldn't find anything matching my specific problem. If it does exist, feel free to link me and flame on with the "search noob." ;)

However, I have one main problem.

1.) I cannot for the life of me get Twinview working for Ubuntu 9.04 x64

I have an older laptop, a Compaq Presario V6101US with an Nvidia GeForce 6150Go. However, the backlight on this laptop is out, and the only way I can see any image on the screen is to hold a flashlight to it. I installed Jaunty with no problems whatsoever, and it seems to run perfectly fine (albeit with no display.)

This is where my 17" Sony CRT (With VGA inputs) monitor comes handy. Prior to installing Ubuntu, I had a corrupted version of XP that wouldn't complete the boot process yet I could see the desktop fine before it froze. But, in Ubuntu I can see grub, and the boot sequence (the Ubuntu Logo with a progress bar) but upon entering the desktop, instead of seeing the orange-brown color scheme I can sort of make out on the LCD, I see blue and orange vertical bars flickering across the screen, like so:

[IMG]http://i2.photobucket.com/albums/y12/glenn8friedrice/UbuntuDesktop.gif[/IMG]

I've researched "twinview" and tried updating the nvidia glk drivers as documented in the Ubuntu Community Help here: 
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?p=1773584](http://ubuntuforums.org/showthread.php?p=1773584)

But to no avail. I've also checked the Hardware Drivers, and it lists nothing.

Here's my xorg configuration:
[SIZE=2]```

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Option "Twinview" "True"
        SubSection "Display"
                Virtual 1280 800
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        option "RenderAccel" "True"
        option "usedisplaydevice" "crt"
EndSection
```[/SIZE] 

Can a Linux newbie get some help? Perhaps a walkthrough?

Additionally, I have a spare keyboard and mouse laying around, if I wanted to simply run the laptop as a personal computer, with the lid shut, and use the external keyboard and mouse how would I make this possible?

Thanks for reading! Hoping to receive a helpful response.

---

### Post by HDave on 2009-05-19
You may think this is stupid, but it worked for me when I was in the same situation (different nvidia gpu though).

1. Turn the laptop off.
2. Plug in the external monitor.
3. Open the lid on the laptop.
4. Turn the laptop on.
5. Shut the lid really quickly before the BIOS screen shows up

VIOLA -- on my laptop it just defaults to the external monitor.

If my leave my laptop lid open, it tries to use that.

If this fails, then try editing your xorg.conf file to look like mine which defaults to using the external monitor.

```
# added by me for proper support of external monitors
Section "Screen"
	Identifier     "Screen0"
	Device         "Default Device"
	Monitor        "Monitor0"
	DefaultDepth    24
	Option         "Coolbits" "1"
	Option         "TwinView" "0"
	Option         "TwinViewXineramaInfoOrder" "CRT-0"
	Option         "metamodes" "CRT: nvidia-auto-select +0+0"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


```

Good luck!

---

### Post by Glenn8Friedrice on 2009-05-23
Thanks for your input Dave. The funniest thing is, I tried exactly what you had said about the process of opening the lid, closing it, etc. Before you had posted this, so eventually I ended up reading this from my newly working Gnome desktop! 

Thanks again for your efforts.

---

### Post by HDave on 2009-05-23
I am SO glad it worked...and even happier that you didn't give up and figured it out yourself!

---

