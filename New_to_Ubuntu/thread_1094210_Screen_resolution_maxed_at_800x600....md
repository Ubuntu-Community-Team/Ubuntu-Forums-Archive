---
title: "Screen resolution maxed at 800x600..."
date: 2009-03-12
forum: New to Ubuntu
---

### Post by craigsavage on 2009-03-12
I switched to my laptop from Vista to Ubuntu 8.10 a few days back. Most things seem to be running fine except for the fact that my screen will only run at a maximum resolution of 800x600, which is much too small. It will run at a higher resolution if I have a second monitor plugged in the VGA output - but that's not too handy a solution for a laptop.

I've been trying out various things I've found in other forum posts of people who seem to be running into a similar problem, but to no avail. Also, I'm a complete beginner so I'm kind of poking around in the dark here.

A bit of basic information:

lspci | grep VGA

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)


Contents of xorg.conf

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


I tried running "sudo dpkg-reconfigure xserver-xorg" but that didn't change anything.

Banging head against computer here. 

Help? Pretty please.

---

### Post by overdrank on 2009-03-12
Hi and welcome, I do not have much experience with the SIS chipset but you may look [[COLOR="Red"]here[/COLOR]]("https://wiki.ubuntu.com/X/Config/Resolution").

---

### Post by craigsavage on 2009-03-12
Hello. I tried everything there and nothing had any effect. Admittedly, I didn't try the last solution - the 'setting resolution changes in xorg.conf' - because I'm baffled as to how I'd get from my empty xorg.conf to anything resembling their example.

I'm currently sitting with my laptop at 1024x768 having plugged a monitor into it. I just can't figure out what is happening differently when there's something in the VGA output. Or why.

---

### Post by martrn on 2009-03-12
A valid xorg.conf, ubuntu 8.10 ignores the input devices that are present as now ubuntu uses hotplug method for keyboards rather than looking at your xorg.conf files and is ignores.  Hotplug will pick up your keyboards, and any usb keybords you also plug in.  SO just concentrate on the module section / device section / monitor section and ignore input devices.

```
Section "Module"
	Load  "freetype"
        Load  "sisfb"
EndSection


Section "Device"
	Identifier  "Built-in Video"
	Option "ForceCRT1"
	Driver      "sis"
EndSection

Section "Monitor"
Identifier "Built-in LCD"
	HorizSync    28.0 - 72.0
	VertRefresh  43.0 - 60.0
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Built-in Video"
	Monitor    "Built-in LCD"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1024x768" "800x6008" "640x480"
	EndSubSection
EndSection
```

Try: 

```
sudo modprobe sisfb
```

in a virtual terminal, then switch back to the normal terminal and ctrl-alt-bkspce to restart x.

---

### Post by craigsavage on 2009-03-12
Hello.

I tried the sudo modprobe thing earlier. It had no discernable effect.

I tried putting your code into my xorg.conf. When I restarted my computer I got an error message:
Failure to load module 'sisfb' (module does not exist)
No devices detected

It then ran in 'low graphics mode'.

---

### Post by overdrank on 2009-03-12
> **craigsavage said:**
> Hello.

I tried the sudo modprobe thing earlier. It had no discernable effect.

I tried putting your code into my xorg.conf. When I restarted my computer I got an error message:
Failure to load module 'sisfb' (module does not exist)
No devices detected

It then ran in 'low graphics mode'.

ok you may try the xfix option when booting into recovery mode. Recovery mode is usually the second choice when booting grub. Then when the xfix option is complete you should be given the option to boot normally.

---

### Post by IsmailBhai on 2009-03-12
try this

sudo apt-get install --reinstall gdm, nautlius, ubuntu-desktop, x-gnome-session, xserver-xorg

sudo update-alternatives --configure x-session-manager

source: [http://hydtech.wordpress.com/2009/02/26/gnome-display-manager-problems-error-setting-mtrr-in-ubuntu-intrepid-810/](http://hydtech.wordpress.com/2009/02/26/gnome-display-manager-problems-error-setting-mtrr-in-ubuntu-intrepid-810/)

---

### Post by craigsavage on 2009-03-17
Just to say thanks for helping out. Sorry it took a while to reply - my wireless isn't currently working (that's another problem) and I don't have a wired internet connection of my own.

I finally managed to fix this problem using the driver provided in this thread [here]("http://ubuntuforums.org/showthread.php?t=958967&page=4")

Though I've only just installed it so I'll have to see if I run into any problems with it.

---

