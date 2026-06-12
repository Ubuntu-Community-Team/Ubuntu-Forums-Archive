---
title: "Help: Nvidia Drivers Needed?"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by frs89 on 2009-07-30
Hi,

I've just installed ubuntu 9.04 and I don't know if I need any driver for my graphics card (Nvidia Go 7300), how and where do I get them? Where do I change monitor parameters? (i.e gama correction, refresh rate, contrast..), because I only know how to adjust brightness..

Thanks.

---

### Post by wojox on 2009-07-30
Look in System > Administration > Hardware Drivers

See if it's enabled.

---

### Post by ktechkio on 2009-07-30
See Nvidia's site [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Save in home folder. Rename to nv.run

The boot in recovery mode. Choose drop to shell. The enter sudo sh nv.run
Choose everthing that lets installer proceed. Then last choose yes for config. Reboot and you're done!:popcorn:

---

### Post by afroman10496 on 2009-07-30
Just press ESC when you are at the GRUB 3-second timeout

---

### Post by Taylor13 on 2009-07-30
You have 3 options:

1. Use the software only 'nv' driver. This is what you currently have. 
2. Use a proprietery NVidia driver packaged with Ubuntu. This is what wojox is refering to and may be easiest. 
3. Use a proprietery NVidia driver directly from NVidia. This what ktechkio is refering to. This what I use. 

If you do decide to go with option 3 you will need to install the kernel headers and build-essential. You can also build it without rebooting by getting to a text terminal (ctrl-alt-F1), logging in and issuing :
```
$ sudo /etc/init.d/gdm stop
```

Or kdm for KUbubtu or xdm for XUbuntu. Build the drivers, alter your Xorg config and then restart gdm.

---

### Post by ktechkio on 2009-07-30
> **Taylor13 said:**
> You have 3 options:
```
$ sudo /etc/init.d/gdm stop
```Or kdm for KUbubtu or xdm for XUbuntu. Build the drivers, alter your Xorg config and then restart gdm.

In Kubuntu just select menu, console login.

The 3rd option in the best. It can also be acheived. With sudo apt-get install envyng.
Then ALT + F2 and type envyng-gtk. (I prefer the first method I mentionned in earlier post) Have Geforce 8500 1Gb

The former command should be launched by oppening Terminal. In Kubuntu start and search konsole. In Ubuntu/ Xubuntu Start accesories, terminal.

---

### Post by daimaru on 2009-07-30
> **frs89 said:**
> Hi,

I've just installed ubuntu 9.04 and I don't know if I need any driver for my graphics card (Nvidia Go 7300), how and where do I get them? Where do I change monitor parameters? (i.e gama correction, refresh rate, contrast..), because I only know how to adjust brightness..

Thanks.
ok wtf boot hit esc install all kinds of crap whats up guys??? 

@frs89 if you dont have the 3d accelerated nvidia drivers installed got to "System > Administration > Hardware Drivers" select "Nvidia accelerated graphics driver (version 180 [Recommended]) and hit install. 

Then reboot for it to take effect. or use ctrl+backspace (if you enabled it in jaunty) else do 
```
sudo /etc/init.d/gdm restart
```

Open Terminal "Applications > Accesories>Terminal" and type in 
```
sudo apt-get install nvidia-settings
```Now you can adjust all you nvidia settings (gamma etc) from "System > Administration > Nvidia X Server Settings". 

If you want to save changes to xorg.conf file you have to start nvidia-settings as super user from console , or edit your menu shortcut and add an gksu.
```
sudo gksu nvidia-settings
```

---

