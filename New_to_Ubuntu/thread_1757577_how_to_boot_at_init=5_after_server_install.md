---
title: "how to boot at init=5 after server install?"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by jmborr on 2011-05-13
Dear Ubuntu lovers,

I installed Ubuntu as server and then installed the desktop:
#sudo apt-get update
#sudo apt-get install ubuntu-desktop

Now what do I have to do to automatically boot at init=5? I still am presented with the terminal after booting.

-jmborr

---

### Post by astex on 2011-05-13
You should edit your /boot/grub/grub.cfg and add init=5 to whichever kernel you choose.  It's quite possible though, that you are, in fact, in runlevel 5 but have not loaded a display manager.  Try 'startx'.

---

### Post by lykwydchykyn on 2011-05-13
Runlevels in Ubuntu are not the same as RedHat or Suse; runlevel 5 means nothing different (unless you have specifically configured it to be so).

If you install the ubuntu-desktop package it *should* automatically boot to the GUI.  If it's not, try this command:

```

sudo update-rc.d gdm start 99 2 3 4 5 .

```

If that's not getting you a GUI, you probably have a graphics driver issue.  Try running "startx" at the command line and see if it is giving errors.

---

### Post by jmborr on 2011-06-05
> **lykwydchykyn said:**
> If that's not getting you a GUI, you probably have a graphics driver issue.  Try running "startx" at the command line and see if it is giving errors.

Thanks for your help. Definitely some drivers are missing. This is the crutial output of "startx":

(==) Using system configuration directory "/usr/share/X11/xorg.conf.d"
(EE) Failed to load module "nvidia" (module does not exists,0)
(EE) Failed to load module "nouveau" (module does not exists,0)
(EE) Failed to load module "nv" (module does not exists,0)
(EE) Failed to load module "vesa" (module does not exists,0)
(EE) Failed to load module "fbdev" (module does not exists,0)

I am a complete ignorant, how do I get a hold of these drivers? :confused:

---

### Post by lykwydchykyn on 2011-06-05
Other than the "nvidia" driver, the rest of those are bundled with xorg.  Sounds like xorg did not completely install.  Can you try:

```

sudo apt-get install xorg xserver-xorg-video-all

```

Watch for any errors during the install, and post here if you get them.

---

### Post by jmborr on 2011-06-06
> **lykwydchykyn said:**
> Can you try:

```

sudo apt-get install xorg xserver-xorg-video-all

```


Definitely an improvement after I installed xserver-xorg-video-all (xorg was already installed). No errors while installing.

I ran "startx" afterwards, a pop-up window showed me the following message:
"*You do not have the hardware required to run Unity. Please choose Ubuntu classic at the login screen and you will be using the traditional environment*"

I assume the reason for the pop-up is I don't have nvidia driver installed. At least now the computer starts with the X-server, but there's no option to choose "Ubuntu classic" at the login screen :)

I also tried to navigate the desktop menu. When I clicked the "System" tab, the computer crashed and ended up with a frozen console. I think it's a kernel panic but I have no way to know because the top portion of the message does not show up in the console, too many lines in the message.

I'll have to install the nvidia-drivers from the console. How do I find out the proper nvidia driver for my computer?

**Update**: I rebooted and now I was able to access Menu->System->Additional drivers, and installed nvidia from there.
I rebooted and did the same (Menu->System->Additional drivers). The popup window says "*the driver is activated but not currently in use*" :confused:

```
cat /etc/X11/xorg.conf
```
Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

```
less /var/log/Xorg.0.log
```
[    20.566] (==) Using config file: "/etc/X11/xorg.conf"
...
[    20.756] (II) LoadModule: "glx"
[    20.756] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    21.686] (II) Module glx: vendor="NVIDIA Corporation"
[    21.686]    compiled for 4.0.2, module version = 1.0.0
[    21.686]    Module class: X.Org Server Extension
[    21.686] (II) NVIDIA GLX Module  173.14.30  Thu Apr 14 09:20:02 PDT 2011
[    21.686] (II) Loading extension GLX
...
[    21.821] (II) NVIDIA dlloader X Driver  173.14.30  Thu Apr 14 08:56:42 PDT 2011
[    21.822] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    21.822] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[    21.822] (II) NOUVEAU driver for NVIDIA chipset families :
[    21.822]    RIVA TNT    (NV04)
[    21.822]    RIVA TNT2   (NV05)
[    21.822]    GeForce 256 (NV10)
[    21.822]    GeForce 2   (NV11, NV15)
[    21.822]    GeForce 4MX (NV17, NV18)
[    21.822]    GeForce 3   (NV20)
[    21.822]    GeForce 4Ti (NV25, NV28)
[    21.822]    GeForce FX  (NV3x)
[    21.822]    GeForce 6   (NV4x)
[    21.822]    GeForce 7   (G7x)
[    21.822]    GeForce 8   (G8x)
...
[    21.851] (II) NVIDIA(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    21.851] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    21.851] (==) NVIDIA(0): RGB weight 888
[    21.851] (==) NVIDIA(0): Default visual is TrueColor
[    21.851] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.851] (**) NVIDIA(0): Option "NoLogo" "True"
[    21.852] (**) NVIDIA(0): Enabling RENDER acceleration
[    21.852] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    21.852] (II) NVIDIA(0):     enabled.
[    22.417] (II) NVIDIA(0): NVIDIA GPU GeForce FX 5500 (NV34) at PCI:1:0:0 (GPU-0)
[    22.417] (--) NVIDIA(0): Memory: 131072 kBytes
[    22.417] (--) NVIDIA(0): VideoBIOS: 04.34.20.69.51
[    22.417] (II) NVIDIA(0): Detected AGP rate: 8X
[    22.417] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    22.417] (--) NVIDIA(0): Connected display device(s) on GeForce FX 5500 at PCI:1:0:0:
[    22.417] (--) NVIDIA(0):     ViewSonic VA2431 Series (CRT-0)
[    22.417] (--) NVIDIA(0): ViewSonic VA2431 Series (CRT-0): 350.0 MHz maximum pixel
[    22.417] (--) NVIDIA(0):     clock
[    22.418] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    22.418] (==) NVIDIA(0): 
[    22.418] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    22.418] (==) NVIDIA(0):     will be used as the requested mode.
[    22.418] (==) NVIDIA(0): 
[    22.418] (II) NVIDIA(0): Validated modes:
[    22.418] (II) NVIDIA(0):     "nvidia-auto-select"
[    22.418] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    22.419] (--) NVIDIA(0): DPI set to (93, 94); computed from "UseEdidDpi" X config
[    22.419] (--) NVIDIA(0):     option
[    22.419] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    22.419] (II) UnloadModule: "nouveau"
[    22.420] (II) Unloading nouveau
[    22.420] (II) UnloadModule: "vesa"
[    22.420] (II) Unloading vesa
[    22.420] (II) UnloadModule: "fbdev"
[    22.420] (II) Unloading fbdev
[    22.420] (II) UnloadModule: "fbdevhw"
[    22.420] (II) Unloading fbdevhw
[    22.420] (--) Depth 24 pixmap format is 32 bpp
[    22.422] (II) NVIDIA(0): Initialized AGP GART.
[    22.425] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    22.838] (II) Loading extension NV-GLX
[    22.863] (II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
[    22.889] (II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
[    22.889] (==) NVIDIA(0): Backing store disabled
[    22.889] (==) NVIDIA(0): Silken mouse enabled
[    22.892] (==) NVIDIA(0): DPMS enabled

---

### Post by lykwydchykyn on 2011-06-06
Sure looks like the nvidia driver is in use, according to the Xorg log.  Are you able to use Unity at this point?

---

### Post by jmborr on 2011-06-06
> **lykwydchykyn said:**
> Sure looks like the nvidia driver is in use, according to the Xorg log.  Are you able to use Unity at this point?

LOL I had to learn what Unity is yet another desktop (been using Gnome with Red Hat for the last three years)

The optional sessions in the login screen are "Ubuntu", "Ubuntu Classic", and others, but nothing like "Unity". Selecting "Ubuntu" or "Ubuntu Classic" ends up with a Gnome session as far as I know (Menu->System->About Gnome
How can start with Unity?

---

### Post by lykwydchykyn on 2011-06-06
"Ubuntu" is Unity, but it's got an auto-detect so that if your card+driver combo can't handle unity, it gives you classic automagically.

I don't know how to force Unity, unfortunately; maybe someone else does.

---

### Post by jmborr on 2011-06-06
> **lykwydchykyn said:**
> "Ubuntu" is Unity, but it's got an auto-detect so that if your card+driver combo can't handle unity, it gives you classic automagically.

By "Ubuntu Classic" do you mean a Gnome session, among other things?

**Update**: Because I installed Ubuntu server and then apt-get install ubuntu-desktop, it seems Unity was not set as default. I did
sudo apt-get update
sudo apt-get upgrade
and now "Unity" desktop comes up when I log in as "Ubuntu" session!!

lykwydchykyn many many thanks for your invaluable help

---

