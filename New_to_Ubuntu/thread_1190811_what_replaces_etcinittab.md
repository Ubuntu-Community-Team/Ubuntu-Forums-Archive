---
title: "what replaces /etc/inittab?"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by raymondvillain on 2009-06-18
Trying to make my video card work.  Running Jaunty 32 bit with Nvidia 8400 GS that doesn't want to work.

I'm following the instructions ([http://us.download.nvidia.com/XFree86/Linux-x86/185.18.14/README/appendix-i.html](http://us.download.nvidia.com/XFree86/Linux-x86/185.18.14/README/appendix-i.html)) and they want me to edit the /etc/inittab file.  Need to find a line that looks like

id:n:initdefault:

The idea is to find the file that controls the default runlevel.

Well, Jaunty 9.04 doesn't have any such file (/etc/inittab).

What is the name of the file in Jaunty that sets the default runleve?

I know it is not /etc/inittab.

---

### Post by kwacka on 2009-06-18
There should be no need to change init.

try clicking on System --> Administration --> hardware Drivers and see if that sets up nVidia drivers for you (the 8400GS is listed as a supported card).

Failing that, follow these instructions: [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by raymondvillain on 2009-06-18
hardware devices just returns with "no proprietary devices..."

I don't want to change init necessarily, but I wish I knew how to set the runlevel.  Do you happen to know what file in Jaunty controls which runlevel is selected at boot time?

---

### Post by oldos2er on 2009-06-18
See [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

---

### Post by cceron on 2010-03-06
Remove your Desktop Manager (gnome dm in this example ):
sudo update-rc.d -f gdm remove
if you need start your Desktop type: startx
If you want your desktop manager again, install it with Synaptic or apt-get

---

### Post by rnldpj on 2010-04-26
You can edit /etc/init/rc-sysinit.conf
and change the following line:

    env DEFAULT_RUNLEVEL=N

Where N is the default runlevel, change this to match.

---

### Post by srs5694 on 2010-04-26
The purpose of those instructions is to shut down X prior to installing the drivers. In Ubuntu, this is *not* done by changing the runlevels, so those instructions, and the workarounds proposed by some others in this thread, are irrelevant.

If you feel you must install the driver directly from nVidia, you can type this to shut down X:

```

sudo /etc/init.d/gdm stop

```

If you haven't done so already, you'll then have to log into a text-mode console. When you're done, type the same command, but passing "start" rather than "stop".

This probably isn't the best way, though. There are nVidia drivers in the Ubuntu repository, so you should be able to install them that way, which will provide you with automatic updates. Unfortunately, I don't recall precisely which packages you should install, and in fact I believe that detail varies from one video card (or on-motherboard video chipset) to another.

---

### Post by _0R10N on 2010-04-26
> **cceron said:**
> Remove your Desktop Manager (gnome dm in this example ):
sudo update-rc.d -f gdm remove
if you need start your Desktop type: startx
If you want your desktop manager again, install it with Synaptic or apt-get

running
```

sudo update-rc.d -f gdm remove

```
only tells the system to not start the gdm service. You shouldn't install it again to get the service back. You could simply run
```

sudo update-rc.d gdm defaults

```

Kind regards!

_0R10N >>

---

### Post by ibuclaw on 2010-04-26
Thanks for your contribution, however this is an old thread and the OP probably is not looking for a solution anymore.

Closing.
Regards

---

