---
title: "Starting Nvidia Xserver at startup"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by sushrut91 on 2009-12-04
I have set up nvidia xserver to start at startup. But at each boot it shows the control panel window. How can I configure so that the window wont open each time but still xserver will start?

I want to do this as My monitors colour settings are done in the application.

---

### Post by aktiwers on 2009-12-06
> **sushrut91 said:**
> I have set up nvidia xserver to start at startup. But at each boot it shows the control panel window. How can I configure so that the window wont open each time but still xserver will start?

I want to do this as My monitors colour settings are done in the application.

Hi there,

Are you sure you didn't setup "Nvidia X server settings" to start at boot? (if this is the case, remove it from startup as it is simply a settings window)
Normally when you have installed the nvidia drivers, they will be launched automatically on boot. This is defined in /etc/X11/xorg.conf.

But if the driver is installed, you should not have any problem.
To make sure Nvidia is added to your xorg.conf, you could run:
 ```
sudo nvidia-xconfig
```in terminal, which will add nvidia properly to xorg.conf.

---

### Post by arochester on 2009-12-06
I usually run: > gksudo nvidia-settings

---

### Post by sushrut91 on 2009-12-10
I ran this command at startup
gksudo nvidia-settings

The color settings are loaded during each boot. Thanks for the help.

The Nvidia Xserver settings window opens every time on boot. Is there a way so that the command "gksudo nvidia-settings" will execute in the background but the window will not be displayed at startup ??:P

---

### Post by presence1960 on 2009-12-10
> **sushrut91 said:**
> I ran this command at startup
gksudo nvidia-settings

The color settings are loaded during each boot. Thanks for the help.

The Nvidia Xserver settings window opens every time on boot. Is there a way so that the command "gksudo nvidia-settings" will execute in the background but the window will not be displayed at startup ??:P

That is impossible as that command specifically invokes the settings window to display.

---

### Post by RedSingularity on 2009-12-11
You dont need  gksudo nvidia-settings to run at start up.  That is just a tool used to configure the driver.

---

