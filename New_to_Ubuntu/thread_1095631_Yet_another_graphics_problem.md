---
title: "Yet another graphics problem"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by The-IRS on 2009-03-13
Hi all.
I just installed the 180.29 graphics drivers for my new Nvidia GTX 260 :P
But, after install I rebooted and it said that it couldn't start the Nvidia Kernel and to check whether the Nvidia config filed were installed properly! So here I am, Running in low settings mode. Please help!

---

### Post by The-IRS on 2009-03-14
Kay. I fixed the resolution but when I run nvidia-xconfig it gives me this error:

```
stewart@Stewarts-desktop:~$ sudo nvidia-xconfig
[sudo] password for stewart: 

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

sh: pkg-config: not found
sh: pkg-config: not found
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

any Ideas? 

and when I try to run the Nvidia X server settings it says:

```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
```

---

### Post by Shazaam on 2009-03-14
Look at this in your etc/X11/xorg.conf (your values/names will differ)...```
Section "Device"
   Identifier     "Card0"
   Driver         "nvidia"
   VendorName     "nVidia Corporation"
   BoardName      "G70 [GeForce 7800 GS]"
EndSection
```
Under "Device>Driver" nvidia should be listed.

---

