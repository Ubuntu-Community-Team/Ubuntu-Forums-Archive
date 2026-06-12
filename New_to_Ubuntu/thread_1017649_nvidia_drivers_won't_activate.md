---
title: "nvidia drivers won't activate"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by sausages on 2008-12-21
Recently when I started up my computer I was met with a warning that the nvidia drivers weren't working so I continued on in safe mode. I checked my hardware drivers and the nvidia drivers box was green, so I decided to try to deactivate them and activate them again to see if it would work properly again, but now I can't activate them. My wireless has suddenly stopped working, which isn't making things any easier. When I try to reactivate the drivers it says "downloading and installing driver." Am I to assume that when I deactivated my driver it uninstalled it? All I get as a warning is a red circle with a slash through it, no words. I've lost 2 days of work over this issue and really need to get things working posthaste.

---

### Post by gettinoriginal on 2008-12-22
It may be that the driver has been updated, try this in terminal:

sudo apt-get update

Then try the System > Admin > Hardware Drivers again.

---

### Post by Duck2006 on 2008-12-22
When your system did an updata did it updata the kernel?
If so your have to reinstall the drivers again.

---

### Post by Bölvaður on 2008-12-22
It also might worth the try to pick an older kernel from grub (the menu at the start of your computer) and see if it will make the drivers kick back in.

If breaking and repairing stuff is fun, then laptop manufacturers are equivalent to the circus.

---

### Post by sausages on 2008-12-22
Thanks for the replies, I get this warning when starting nvidia server settings: "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root) and restart the x server." 
When I run the xconfog file I get this "validation error: data incomplete in file /etc/X11/xorg.conf. Device section "configured video device" must have a driver line."
 Bear in mind I have no direct internet hook up, but I can download the appropriate debs, burn them to a cd, and transfer them. I've tried on 2 different kernels with no luck, and tried reinstalling the drivers, but I am new at this so I may have missed something- like deleting the old ones first!

---

### Post by mgmiller on 2008-12-22
> Device section "configured video device" must have a driver line."Can you post your /etc/X11/xorg.conf file here?

Open a terminal and post the output of:
```
cat /etc/X11/xorg.conf
```Specifically, we are looking for the Section "Device" portion.

This is what mine looks like.  I am using the nvidia driver:
```
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection
```Edit:
To save some time, here is what you can try:

First, backup the original file:
```
sudo cp /etc/X11/xorg.conf xorg.backup
```Now, if everything goes to heck, you can restore your original setup by typing:
```
sudo cp /etc/X11/xorg.backup xorg.conf
```Next, open the file for editing:
```
gksu gedit /etc/X11/xorg.conf
```scroll down to the Section "Device" area and edit it to look like mine above:
```
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection
```Save the file and reboot.

(Or you could log off and back on and it might just reinitialize)

I won't be back till sometime tomorrow, so, hopefully, this will get you going.

---

### Post by Dissociated State on 2009-02-21
I'm having a similar problem. I've been using the NVIDIA (version 96) driver on 8.10 for a number of months, but its just suddenly stopped working.

Here's the section "device" portion mgmiller's talking about.

Section "Device"
	Identifier     "Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

When I try opening the file for editing using "gksu /etc/X11/xorg.conf" it doesn't open.

I've tried running 'nvidia-xconfig' as root and restarting the x server but it didn't make any difference. When it says " please edit your X configuration file", what does this actually involve?

These nvidia cards are a pain in the ***!

Any help would be greatly appreciated.

---

### Post by mgmiller on 2009-02-21
> When it says " please edit your X configuration file", what does this actually involve?

That means editing the xorg.conf file as described earlier.

> When I try opening the file for editing using "gksu /etc/X11/xorg.conf" it doesn't open.

That's because the command should read:
```
gksu gedit /etc/X11/xorg.conf
```

I will edit my instructions to reflect the error.

Sorry about that chief...

---

### Post by Dissociated State on 2009-02-21
ok tried changing the xconfig file device section to read like yours but still no luck. Any other ideas?

How do you think it deactivated itself in the first place?

---

### Post by mgmiller on 2009-02-21
What video card do you have?
Enter this command to find out:
			 				```
lspci -x | grep -i "vga\|display"
```

What is showing up in System > Administration > Hardware Drivers?
Have you tried changing between the different choices there?

Have you tried disabling all the choices so it uses the open source driver and then rebooting and re-enabling the different choices?

Have you also tried doing:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

That sometimes clears up dependency issues with kernel modules and glx stuff.

---

### Post by zero244 on 2009-02-21
I think you need to reinstall the drivers.
When I first started using Hardy, it suddenly stopped recognizing my video card.
I had to reinstall Hardy to fix the problem. I haven't had any further video problems since.

You might try downloading and installing Envyng.
First uninstall the drivers using Envyng then reinstall.

---

### Post by mgmiller on 2009-02-21
Another thing you can try is during boot up, when it pauses at the grub screen, hit one of your up or down arrow keys to stop the count down and give you time to read the grub screen to figure out what you want to do.  There is a choice to fix video, which will redetect the video card and reset it to the open source driver.    You can then try the hardware drivers utility again to set the one you want.

---

