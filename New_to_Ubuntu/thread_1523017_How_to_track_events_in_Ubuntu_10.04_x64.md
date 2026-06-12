---
title: "How to track events in Ubuntu 10.04 x64"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by NarizWallace on 2010-07-03
Hello Ubunters,

A few days ago I installed Ubuntu 10.04 in my Inspiron 1564 (Core i3), looks like I have all my hardware working correctly, I also configured Compiz effects, MonoDevelop, Gimp, VLC Media Player, Google Chrome, Flash Player and Dropbox and I've uninstalled Rhythm Box and Evolution.

I've configured my Wireless card by using the proprietary drivers.

I don't know what is wrong with my installation, when I upgraded my systems everything looked just fine, I didn't upgrade the Kernel so my system is still working with 2.6.32-21-generic, the problem comes up when I'm using a few applications at the same time (Firefox, Google Chrome, MonoDevelop, Terminal, etc) suddenly the system goes freeze and nothing responding anymore, so I must turn the laptop off.

I'm stuck trying to figure out whats is wrong in my box, is there a way to track the latest events and see something like an error message or exit code?

I know there is a log viewer at System -> Administration -> Log File Viewer, but I'd like to have a more specific answer, tip or advice.

I also know that I can start application in a terminal and put their messages in a log file, something like this: monodevelop > monodev.log, I did that with a few applications but I didn't find anything, so I think the problem could be in an application that is running in background.

Please keep in mind that I'm a newbie. Thanks for any help.

---

### Post by bodhi.zazen on 2010-07-03
This kind of problem can be difficult to solve.

Potential problems could come from your proprietary drivers, either nvidia / ati or your wireless driver.

Can you try a wired connection for a while and see if it is the wireless driver ?

Your other option would be to not use the nvidia / ati driver. Your resolution would be poor, but if you could identify the problem with either driver.

It would also help if you gave us more detailed information.

What video driver are you using ?

How much RAM do you have ?

What wireless card are you using ? Are you using encryption (WEP / WPA) ?

---

### Post by NarizWallace on 2010-07-04
thanks bodhi.zazen,

During the installation all my hardware (Bluetooth, ethernet, video, soundcard, and other) was configured without problem but wireless.

Wireless card is working with its propietary driver, see details:

Broadcom STA wireless driver: These package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware (Dell Wireless 1520).

I forgot to mention that my laptop have no graphics cards it just has a Intel Graphics Media Accelerator HD Driver.

My system is working with 4GB of RAM.

Now I'm working with a wired connection, so far any failure.

I appreciate your help

---

### Post by bodhi.zazen on 2010-07-04
> **NarizWallace said:**
> thanks bodhi.zazen,

During the installation all my hardware (Bluetooth, ethernet, video, soundcard, and other) was configured without problem but wireless.

Wireless card is working with its propietary driver, see details:

Broadcom STA wireless driver: These package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware (Dell Wireless 1520).

I forgot to mention that my laptop have no graphics cards it just has a Intel Graphics Media Accelerator HD Driver.

My system is working with 4GB of RAM.

Now I'm working with a wired connection, so far any failure.

I appreciate your help

If it works with wired, but locks with wireless, that at least helps isolate the problem.

I would try wireless again and see if that indeed seems to be the source of your problems.

---

