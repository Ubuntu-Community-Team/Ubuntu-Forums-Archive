---
title: "Ubuntu 8.04.4 &amp; Nvidia Driver Removal Help!"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by lkraemer on 2010-05-05
I booted my Desktop and checked the Hardware Drivers to see if the 
Nvidia Video card had drivers available.  There was a Video driver
available and I clicked on Install the driver.

Nvidia-GLX-NEW was downloaded & installed, and after a restart I have no
video on the Monitor.  And therefore I can't do a thing.  I can get to
a Terminal Window by CNTL ALT F1.

Can someone please help me get my Ubuntu 8.04.4 booted, and get this driver
removed so my system is once again usable.

Thanks.

lk

---

### Post by evil_urna on 2010-05-05
> **lkraemer said:**
> I booted my Desktop and checked the Hardware Drivers to see if the 
Nvidia Video card had drivers available.  There was a Video driver
available and I clicked on Install the driver.

Nvidia-GLX-NEW was downloaded & installed, and after a restart I have no
video on the Monitor.  And therefore I can't do a thing.  I can get to
a Terminal Window by CNTL ALT F1.

Can someone please help me get my Ubuntu 8.04.4 booted, and get this driver
removed so my system is once again usable.

Thanks.

lk

If you can get into terminal then you will want to purge the "new" driver.

```
sudo apt-get purge nvidia-glx-new
```

and then reinstall the legacy driver from the system>admin>Hardware Drivers menu if you can

---

### Post by lkraemer on 2010-05-06
OK, I have the nvidia-glx-new driver removed, but that now has my
screen Resolution to 800x600.

I downloaded the Nvidia driver for my 8200 Nvidia card, and tried
installing the script.  It had a dependency error of needing libc.
I installed build-essential, then ran the script.

But now I still get 800x600 resolution.  For some reason I can't
get it back to what it was.

I searched and found the following command:
sudo dpkg-reconfigure xserver-xorg -phigh

I ran that and restarted gdm with:
sudo /etc/init.d/gdm start

And my resolution is 1280x1024 but I get this error when I try to use
Synaptics:

Failed to run /usr/sbin/synaptic as user root
unable to copy the user's xauthorization file.

And I haven't a clue as to what it is telling me.

I need specific instructions....PLEASE!

lk

---

### Post by lkraemer on 2010-05-06
FIXED!

Reference:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)


If you are NOT in the GUI (maybe you have a blank screen after boot-up)
Do CTRL+ALT+F1 to get to a tty, and login with your username and password.
Then depending on your desktop environment, run
For Gnome (Ubuntu) = gdm:   Kubuntu= kdm   XFCE=xdm
```

sudo /etc/init.d/gdm stop

```

Run the reconfiguration
First start by making a manual backup (even though one will be auto-generated
in the form xorg.conf.YearMonthDayTime):
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```
Now run the configuration:
```

sudo dpkg-reconfigure xserver-xorg -phigh

```

Restart the GUI

You are in a tty, so run:
```

sudo /etc/init.d/gdm start

```

Then restart X.
```

startx

```

lk

---

