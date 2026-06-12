---
title: "Using HDTV through HDMI as secondary display in 64 Bit Ubuntu 10.04"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by mfdali01 on 2011-04-16
I am completely new to ubuntu.

I installed ubuntu through a USB Flash drive created from downloaded ISO.

I have a AOC 24" [COLOR=Red]HDTV[/COLOR] which I want to use [COLOR=Red]as a secondary display in 64 BIT Ubuntu 10.04[/COLOR], mainly for the purpose of watching movies, listening to music. But I have a [COLOR=Red]problem with connecting my laptop to the HDTV through HDMI. [/COLOR]I am [COLOR=Red]not able to get the native resolution of the HDTV (1920 x 1080)[/COLOR].  It does display the desktop but the top panel, desktop icons and the  bottom panel are not visible. The Audio works fine. This worked completely fine with Win7. Details as under :

Laptop Configuration :
Model : Toshiba E105-S1402
Intel Core2Duo P8400 2.26 Ghz.
4 GB DDR2 800 Mhz RAM
320 GB HDD
[COLOR=Red]Intel GMA4500HD Integrated Graphics[/COLOR]
Intel HD Audio (HDMI)
Realtek ALC 268 Audio
DVD Writer
Intel ICH9 Chipset
Ricoh Card Reader
Chicony Webcam
Synaptics Touchpad

I hae not installed any extra drivers.

Secondly, I am [COLOR=Red]not able to connect to the internet using my Nokia N82 via Bluetooth[/COLOR]. It [COLOR=Red]works with a usb cable[/COLOR]. And it also used to work via bluetooth with Ubuntu 10.10.

Please, Please, Please give me solutions to these because I have been  using windows 7 for almost 2 years and just do not want to go back to  Windows.

Also, give [COLOR=Red]suggestions for using Nokia N82 as a Bluetooth Phone Remote Control.[/COLOR]

---

### Post by bryanl on 2011-04-16
in system->preferences->monitors you can see the detected monitors, set their display resolution, and determine whether the second monitor just echoes the first or serves as additional desktop space. If set no to image, you can drag the monitors around to the configuration you want.

You might also look in preferences for bluetooth settings but that one is out of my experience. good luck!

---

### Post by mfdali01 on 2011-04-17
Thanks Bryan for your help.

Unfortunately, the scene is such that I can only mirror the two monitors (the laptop display & the HDTV). It does not take the HDTV as a separate display. Which consequently leads to improper resolution on the HDTV. If I move around the displays in the Monitors Panel and set the resolution of the HDTV manually to 1920*1080, I can only see the desktop wallpaper without the panels and desktop icons. I think some people have been referring to this as overscaling. But, cannot find a way out.

About the bluetooth connection with Nokia N82 for internet connectivity, I was able to do this with Blueman Bloetooth Manager, but suddenly it stopped working on my laptop and the native bluetooth manager of ubuntu 10.04 does not help in this matter.

Thanks once again and Best Regards,

---

### Post by K_45 on 2011-04-17
Can you try this with Ubuntu 10.10 if the Bluetooth worked? For the monitor open a terminal and enter

```
gksu jockey-gtk
```

Activate the driver and reboot. Result?

---

