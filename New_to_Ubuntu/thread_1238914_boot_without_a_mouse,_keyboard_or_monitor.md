---
title: "boot without a mouse, keyboard or monitor"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by klein de usa on 2009-08-12
hi 
	i would like to set up ubuntu 8.04 on a computer then have it start up with out a keyboard or mouse or monitor, then i can remote into it from another computer over the internet, i guess what i'm asking for is for it to load the drivers without the devices being there or copy the original set up monitor, keyboard and mouse and load those without them actually being connected to the computer. is this possible?

---

### Post by Hospadar on 2009-08-12
Yep,
Once the machine is set up, it really has no need for any of those things.  If you can remote into with some method of your choosing, then you're all good.

---

### Post by klein de usa on 2009-08-12
hi 
i have a kvm switch and if the kvm switch isn't set to the computer that is booting then ubuntu doesn't load the video right because it doesn't see a monitor loads a very low resolution, is there a way around that problem is there something i can disable, or change

---

### Post by Wim Sturkenboom on 2009-08-13
A decent KVM switch should pass the info from the monitor to any connected computer when the computer requests that information. I'm not sure if decent KVM switches exist.

You can manually configure /etc/xorg.conf. Search this forum for *useedid*, *horizsync* and *vertrefresh*.
See e.g. [http://ubuntuforums.org/showthread.php?t=1212935](http://ubuntuforums.org/showthread.php?t=1212935)

---

### Post by mystmaiden on 2009-08-13
I have a really inexpensive kvm and it works like a charm, not sure why  a decent one wouldn't exist?

myst

---

### Post by Wim Sturkenboom on 2009-08-13
> **mystmaiden said:**
> I have a really inexpensive kvm and it works like a charm, not sure why  a decent one wouldn't exist?

The only time that I have used one was a while ago and my xorg.conf was hard coded. But I'm glad to know that decent ones do exist.

---

### Post by Zack McCool on 2009-08-13
> **klein de usa said:**
> hi 
i have a kvm switch and if the kvm switch isn't set to the computer that is booting then ubuntu doesn't load the video right because it doesn't see a monitor loads a very low resolution, is there a way around that problem is there something i can disable, or change

If you're planning on using it headless, don't even have it load gdm at boot.  Have it boot text-only, and install nxserver or freenx on it for remote use.  You'll have a much better remote experience, IME.

---

