---
title: "uninstalled nvidia driver now x won't start"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by occams_beard on 2009-02-27
I had manually installed the latest nvidia driver from nvidia's website.  But I had some problems with it and my dual monitor set up, so I wanted to go back to the old restricted driver from apt.

I ran "NVIDIA_Linux* --uninstall" and it uninstalled the driver. However after rebooting when X starts all I get is black screen. It just sits there doing nothing. GDM doesn't load and I can't even do a ALT + F1  to get another tty console.

I've tried booting into the recovery console and telling it to fix X. That didn't work.

I've also tried running these as root from the recovery console without success:
dpkg --configure -a
dpkg-reconfigure -phigh xserver-xorg
dpkg-reconfigure gdm

Please help!

---

### Post by smani on 2009-02-27
You could try to manually reinstall the restricted driver that comes with ubuntu
```
sudo apt-get install nvidia-glx-177
```
where I am assuming that you have a relatively new nVidia card (GF 6 or above - otherwise you need the -173 or the -71 for really old cards).

Edit: if you installed the new driver manually without previously removing the standard one, you might have to first remove that package - best with sudo apt-get purge, and then reinstall it.

---

### Post by stchman on 2009-02-27
What kind of nvidia card do you have?

---

### Post by occams_beard on 2009-02-27
It's a 9500gt.

I tried installing the 177 driver as suggested and it didn't work.  Same as before.. empty black screen :(

---

### Post by occams_beard on 2009-02-27
At this point I'll even reinstall the nvidia driver that I uninstalled.

However, I can't even do that because the installer requiers runlevel 3.  Doing a telinit 3 as root I get that friggin black screen again.  Is there anyway to make ubuntu NOT start X and log in normally straight from the console?

---

### Post by smani on 2009-02-27
You don't necessarily need runlevel 3, it is sufficient if you stop the gdm (if you are using gnome)
```
sudo /etc/init.d/gdm stop
```

---

