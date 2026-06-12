---
title: "removed the manually installed nvidia driver now the driver manager doent detect card"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by legolas_w on 2009-03-12
Hi
Thank you for reading my post
I installed nvidia driver manually using its sh files now I removed the driver using nvidia-uninstall command and restart the computer. When I restarted it said that I should use generic low graphic mode and I accepted.

Now I am in the Gnome desktop and I want to install the ubuntu provided driver but the "Administration> Hardware Drivers" does not detect my card.

what should I do now?

Thanks

---

### Post by cantormath on 2009-03-12
What kind of card do you have?

try synaptic. to look for the drivers, or in terminal,
 apt-cache search nvidia

It is just a matter of getting the right driver from the repo installed.

---

### Post by sisco311 on 2009-03-12
Yes, you can use the package manager to install the driver.

[uhelp]community/BinaryDriverHowto/Nvidia[/uhelp]

```
sudo aptitude install linux-headers-`uname -r` linux-restricted-modules-`uname -r` nvidia-glx
```

---

### Post by legolas_w on 2009-03-12
> **sisco311 said:**
> Yes, you can use the package manager to install the driver.

[uhelp]community/BinaryDriverHowto/Nvidia[/uhelp]

```
sudo aptitude install linux-headers-`uname -r` linux-restricted-modules-`uname -r` nvidia-glx
```

Hi,
My graphic card is Nvidia 7100gs. I tried the command you gave me and it done some installation but I am still unable to see anything in the Administration > Hardware Drivers.
I barely can read anything on the screen, I think the refresh rate is very low and unfortunately I can not change the refresh rate in the Screen Resolution application, it just shows 0 as the refresh rate.

thanks

---

### Post by sisco311 on 2009-03-12
> **legolas_w said:**
> Hi,
My graphic card is Nvidia 7100gs. I tried the command you gave me and it done some installation but I am still unable to see anything in the Administration > Hardware Drivers.
I barely can read anything on the screen, I think the refresh rate is very low and unfortunately I can not change the refresh rate in the Screen Resolution application, it just shows 0 as the refresh rate.

thanks

edit the xorg.conf file:
```
gksu gedit /etc/X11/xorg.conf
```
and change the driver, in the Device section, from vesa or nv to nvidia .

```
Section "Device"
        Identifier  "blabla"
        Driver      **"nvidia"**
        ...
EndSection

```

restart X (Ctrl+Alt+BackSpace) and try to set the resolution in nvidia-settings:
```
gksu nvidia-settings
```
save the settings in the xorg.conf file (nvidia-settings -> X Server Display Configuration -> Save to X configuration file)

---

