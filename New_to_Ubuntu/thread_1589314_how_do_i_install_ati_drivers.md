---
title: "how do i install ati drivers?"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by Intsmssss on 2010-10-06
I've installed ubuntu 10.04 yesterday with great difficulty because the backlight of my laptop monitor is dead. Ive hooked up a samsung monitor but this diddnt display anything during installation.

Anyway, I did complete the installation and put the resolution on 800 600 with 75hz. If i put it on an other settings the samsung monitor wont display anything. 1024 768 will work for about a minute or so before the monitor shutting down complaining: not optimum mode, recommended mode: 1280 1024 60hz.

Why it doesnt display anything on anything lower then 75hz at the moment is a mystery to me.

I made a topic on this yesterday as well and got the info to install ati drivers using jockey.
I havent been able to do this so far as i cant find a way to open this jockey.

Could anybody please guide me through the installation process?

Im running ubuntu 10.04
Asus A6Ja laptop
Ati x1600 video card

Im sorry for the wall of text and my complete inability to use ubuntu.

PS: system, administration, hardware drivers only shows me a proprietary modem driver which i have activated. Dont know what this does tho since i had Internet before activating this. Here's the driver info:

The SmartLink modem daemon is the application part of thedriver for recent modems produced by Smart Link Ltd.

This package replaces (along with hardware access drivers) the olddriver generation (2.7.x) which consisted of kernel modules only.

It needs a kernel driver to access the hardware. This can be eitherrecent ALSA (shipped with a newer kernel (>=2.6.4) with ALSA supportand snd-intel8x0m module) which is sufficient for basic operation anddata/Internet connection, or the SmartLink kernel driver which isprovided by separate packages which you can build using the source fromthe sl-modem-source package.

This driver enables the usage of many software modems, as commonly found in laptops.

If this driver is not enabled, you will not be able to use your modem.

---

### Post by clhsharky on 2010-10-06
Intsmssss


> Ati x1600 video card
Is legacy for fglrx.

The Ati x1600 is supported with the default installed driver in Lucid, the radeon & open source stack drivers.

Using jockey or ATI proprietary drivers will not work on your chip in Lucid.

Sharky

---

### Post by Mark Phelps on 2010-10-06
The problem is that (1)current ATI proprietary drivers won't work with your card and (2) the older drivers that WILL work with your card won't work with Ubuntu versions newer than 8.10.

So basically, as already said, the open-source drivers are your only option -- and they are installed by default as part of initial setup.

---

### Post by sandyd on 2010-10-06
> **Intsmssss said:**
> I've installed ubuntu 10.04 yesterday with great difficulty because the backlight of my laptop monitor is dead. Ive hooked up a samsung monitor but this diddnt display anything during installation.

Anyway, I did complete the installation and put the resolution on 800 600 with 75hz. If i put it on an other settings the samsung monitor wont display anything. 1024 768 will work for about a minute or so before the monitor shutting down complaining: not optimum mode, recommended mode: 1280 1024 60hz.

Why it doesnt display anything on anything lower then 75hz at the moment is a mystery to me.

I made a topic on this yesterday as well and got the info to install ati drivers using jockey.
I havent been able to do this so far as i cant find a way to open this jockey.

Could anybody please guide me through the installation process?

Im running ubuntu 10.04
Asus A6Ja laptop
Ati x1600 video card

Im sorry for the wall of text and my complete inability to use ubuntu.

PS: system, administration, hardware drivers only shows me a proprietary modem driver which i have activated. Dont know what this does tho since i had Internet before activating this. Here's the driver info:

The SmartLink modem daemon is the application part of thedriver for recent modems produced by Smart Link Ltd.

This package replaces (along with hardware access drivers) the olddriver generation (2.7.x) which consisted of kernel modules only.

It needs a kernel driver to access the hardware. This can be eitherrecent ALSA (shipped with a newer kernel (>=2.6.4) with ALSA supportand snd-intel8x0m module) which is sufficient for basic operation anddata/Internet connection, or the SmartLink kernel driver which isprovided by separate packages which you can build using the source fromthe sl-modem-source package.

This driver enables the usage of many software modems, as commonly found in laptops.

If this driver is not enabled, you will not be able to use your modem.

have you tried shutting off the Laptop display with
```
xrandr --output LVDS --off

```

---

