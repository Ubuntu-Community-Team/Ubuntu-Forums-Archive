---
title: "Screen Resolution Issue with Intel display adapter"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by trinity1188 on 2009-03-12
Hi,

I am having some screen resolution problems within Kubuntu. I have a Sony VGN-FW140E laptop and i am dual booting Vista and Kubuntu. In windows i can have up to 1600x900 resolution but in Kubuntu i am restricted to 800x600. My display adapter is a Intel GMA 4500MHD with an Mobile intel(R)4 Series express driver installed. How can i get a better screen resolution?

Any help would be greatly appreciated! Thanks in advanced.

Here is my xorg.conf file:

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

---

### Post by martrn on 2009-03-12
KDE on ubuntu (kubuntu - same thing) out of the box and uses the GDM (gnome display manager), to start X11.

Depending on the version of ubuntu your are running.  If you are running 8.10 then ubuntu will use hotplugging and the XRandR extension (of the xorg) to auto-magically detect the resolution of your monitor from the hotplug extension of HAL.

There is an Xfix, which will re-fix a broken x11 configuration from the recovery menu of your ubuntu installation.  This is selectable through booting grub and then selecting xfix.

It your new drivers do not support it you need a valid  /etc/X11/xorg.conf  file depicting at the very least the resolution settings of your monitor and you are pretty much on your own, unless someone with the same graphics card has the same problem as you describe.

---

### Post by trinity1188 on 2009-03-13
I tried the Xfix tool in the recovery manager and nothing changed with the resolution. When i first installed kubuntu i had to select the "safe graphics mode" b/c when i chose normal my screen would flicker black and then turn white and slowly fade to grey and then to black. Could i make my own xorg.config file, if so where could i find the appropraite info that the file needs? How would i go about updating my intel driver for the graphics card in kubuntu? Thanks for your suggestions and help!

---

### Post by martrn on 2009-03-13
> **trinity1188 said:**
> I tried the Xfix tool in the recovery manager and nothing changed with the resolution. When i first installed kubuntu i had to select the "safe graphics mode" b/c when i chose normal my screen would flicker black and then turn white and slowly fade to grey and then to black. Could i make my own xorg.config file, if so where could i find the appropraite info that the file needs? How would i go about updating my intel driver for the graphics card in kubuntu? Thanks for your suggestions and help!

Firstly I don't know, I don't have an intel integrated graphics cards, only various flavours of nvidia, on laptops.  Howerer xorg while looking at the xorg.conf files, it will change the xorg.conf at will so is tempremental.  Here are links to valid xorg.conf files see :

[URL="http://ubuntuforums.org/showthread.php?t=903182"]
http://ubuntuforums.org/showthread.php?t=903182[/URL]

Ubuntu is based on debian and there is a guide for installing gnu/linux or debian systems (which ubuntu is derived from) on the computer with the same chipsets, including graphics chipsets that you have.  (I was only roughly checking the specs to your system, not at any great length.)

Here : [http://www.claudiocamacho.org/tech/sr11m_debian.php]("http://www.claudiocamacho.org/tech/sr11m_debian.php").

GNU/Linux or rather the linux kernel has better support for computers that are not quiet so new, your laptop looks like it will has been reviewed very recently and is quiet new.  It takes a while for kernel modules/drivers to be written with newer chip-sets, its possible and when they make it into the kernel they are kept out in the development kernels until they become stable enough for production systems.

I do not have a sony laptop.

---

### Post by blackened on 2009-03-13
Here is a quick rundown on using xrandr to manage your display settings. This is the preferred method till they get a frontend cobbled together (supposed to be scheduled for Jaunty).
[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution").

---

### Post by martrn on 2009-03-13
Also to note there is a bug report stemming pages and pages long about the standard kernel module/driver for your chipset for your graphics card.

[URL="https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bugs?field.tag=xorg"]
https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bugs?field.tag=xorg[/URL]

I only point it out as you ask .."..How would i go about updating my intel driver for the graphics card in kubuntu?.."..

You could type :
```
sudo apt-get install xserver-xorg-video-intel
```

but there is quiet a number of people having problems with it.

---

