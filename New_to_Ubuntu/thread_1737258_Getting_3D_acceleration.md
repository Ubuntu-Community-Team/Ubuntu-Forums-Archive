---
title: "Getting 3D acceleration"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by Vinre on 2011-04-23
Trying to get 3D acceleration through my RadeonHD 5770. I've updated my version of Ubuntu as of a few hours ago, and installed the latest drivers as per the directions here   [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")

After several reboots, a few interesting things happen. 

1. hardware drivers shows ATI/AMD proprietary FGLRX/graphics driver activated and currently in use
2. ~$ glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  18
  Current serial number in output stream:  18

I'm using an AMD motherboard. 

My goal here is to be able to run WoW, but that's an issue for another post. For now, I'd like to be able to figure out what to do from here. It's in use, but there's no 3D acceleration as far as I can tell from terminal... then again, I know nothing.

I've tried uninstalling and redownloading the drivers once already- before trying that, glxinfo gave the error "segmentation fault."

Any help is much appreciated- nothing I've read so far (and I've been at this for 4 hours now with the aid of a much more computer literate boyfriend) has gotten me any closer to a solution. Moslty it's just " type glxinfo |grep something something something and if it says yes, you're golden. if not, well we don't know."

---

### Post by realzippy on 2011-04-23
Have you run

```
sudo aticonfig --initial -f
``` 
after running the ATIxxxx.run file ?

---

### Post by Vinre on 2011-04-23
Yes-

> $ sudo aticonfig --initial -f
[sudo] password for 
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-3


then-

> ~$ glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  18
  Current serial number in output stream:  18

Do I need to restart before trying glxinfo again?

Edit: Restarted anyway, same error. 
When going to Preferences>ATI Control Center, it opens a window, but there really isn't much there: no options to change anything. You can press "OK" or "Cancel." Pressing OK creates no noticeable change (small wonder- no settings were changed!)

---

### Post by Vinre on 2011-04-23
Uninstalled, installed generating a distribution specific driver package, following the directions from the link in the original post. I selected the detected OS which was the appropriate version of Ubuntu, and continued through.

Next it says to install the generated distribution package using the distribution's package management system. 
I have no idea what this means. If it means going into synaptic package manager, there's some other error because there is nothing found by searching for ati. 

This can't be as hard as I'm making it.

---

### Post by khelben1979 on 2011-04-23
> **Vinre said:**
> This can't be as hard as I'm making it.

By doing things too fast without knowing what you're doing makes it harder. You had a working driver from AMD, that 3D acceleration don't work as it should does not necessarily mean that the driver is broken.

The graphics driver must communicate with [the X server]("http://en.wikipedia.org/wiki/X_Window_System") and a good installation should have configured the X server so 3D acceleration should be working. If you understand this part, then knowing and telling us what driver version which you downloaded and which version of Ubuntu helps a lot to figure out what is going on with your system over there.

Slow down the speed and use the man pages for every command you feel uncertain about. Also there are wiki pages which at times can be quite helpful.

I'm not exactly sure how to solve your issues, but understanding how it works is a step in the right direction.

---

### Post by Vinre on 2011-04-23
Yes, I should have included this information initially. 

Drivers: Catalyst 11.1

Ubuntu 10.04

---

### Post by khelben1979 on 2011-04-23
From what I can see, Catalyst 11.3 is available for that graphics card, you might be interested to try it out!

---

### Post by khelben1979 on 2011-04-23
Give us the output from this command to see how it looks like: ```
fglrxinfo
```

---

### Post by realzippy on 2011-04-24
Do you run 32 or 64 bit Ubuntu 10.04 lucid ?
Which kernel do you run?:

```
uname -r
```


Why have you tried installing the ATI driver manually?
Did a former attempt with the driver offered in *Hardware Drivers* fail?

---

