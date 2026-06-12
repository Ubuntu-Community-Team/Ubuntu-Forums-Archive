---
title: "Video Card Drivers"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by jnmjr on 2010-02-22
Hey Guys, I've been having some difficulty with my Video Cards, freezing OS, so I downgraded to an older card... NVidea GS6200... and when I booted a screen came up after Grub giving choices to correct Xconfig, well I didn't know how to do any of that so I continued booting in a sort of safe screen mode and got back in to Ubuntu. I removed the drivers and installed the older drivers for this particular card. Next I proceeded to delete the Xconfig files since they didn't seem to work anyhow. I rebooted thinking with the new drivers a new file would be generated, well the booting went smooth enough but when I went to change the screen resolution this message came up:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

I went back into etc/x11 the only file there is xorg.conf.failsafe the contents of which are:

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

It's obvious no new file was generated with the present drivers.....Can any one help with this? All I want is to be able to change my resolution and that the OS is aware of the drivers. THX

---

### Post by theozzlives on 2010-02-22
With my nVIDIA "6" series I just downloaded the driver from nVIDIA.

---

### Post by jnmjr on 2010-02-22
> **theozzlives said:**
> With my nVIDIA "6" series I just downloaded the driver from nVIDIA.

The drivers are installed it's just that the OS doesn't know it for some reason, I checked in synaptic and it shows they are installed, my question is..... How Do I Get Karmic To See Them? There is a way to change resolution but it throws the screen off center and such, so I have to use the monitor menu to fix it.... that's a pain in the.... and there's no need for it if the OS would recognize the drivers and generate a new Xconfig.  THX.

---

### Post by jnmjr on 2010-02-22
> **jnmjr said:**
> The drivers are installed it's just that the OS doesn't know it for some reason, I checked in synaptic and it shows they are installed, my question is..... How Do I Get Karmic To See Them? There is a way to change resolution but it throws the screen off center and such, so I have to use the monitor menu to fix it.... that's a pain in the.... and there's no need for it if the OS would recognize the drivers and generate a new Xconfig.  THX.


Got it working, THX.

---

