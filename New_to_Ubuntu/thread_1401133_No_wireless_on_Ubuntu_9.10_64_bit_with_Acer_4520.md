---
title: "No wireless on Ubuntu 9.10 64 bit with Acer 4520"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by WWWT on 2010-02-07
Hello dear community,

I am a Ubuntu 1 day old and want to learn about this program since windows has driven me up the wall the (hopefully) last time.

Am having a range of problems which i hope to be able to solve by other posts, but i have a crucial problem with me not getting the wireless connection to run.

I tried out ways to solve the problem posted in various posts but none of them seem to work for me.

Will be very grateful for help of anykind getting me closer.

Greetings,

WWWT

---

### Post by dearingj on 2010-02-07
What solutions have you tried so far?

I'd recommend temporarily connecting to the internet using a wired connection if you can, in order to download any needed software updates and/or drivers.

---

### Post by nhasian on 2010-02-07
make sure the hardware/software switch is ON for your wifi adaptor.  on my HP its a physical switch on the front of the computer.  on other notebooks it may be a key combination like Function-F10 or something similar.  make sure its on.  you should be able to click on the wifi icon on the toolbar and it will show all the WAPs you can connect to.

if your wifi adaptor is not detected, open a terminal from Applications->Accessories->Terminal and enter the command:
(Make sure your connected to the internet via the ethernet adaptor first)

```
sudo apt-get update && sudo apt-get upgrade
```

you may need to reboot.  then check System->Administration->Hardware Drivers

see if there are any drivers you can enable for your network adaptor.


if that fails, give us the output of the terminal command:

```
lshw -C network
```

copy/paste the output here so we can help you troubleshoot.

---

### Post by lockalidiot on 2010-02-07
I had a similar problem at first too. The solution was simply to update the thing. (System -> Administration -> Update Manager)

---

### Post by SoFl W on 2010-02-07
Last week I installed 9.10 (32bit) on my laptop.   While booting I noticed an error displayed for a brief time.  I checked the logs, found the error and it lead me to [**THIS**]("http://ubuntuforums.org/showthread.php?t=759100") thread.  Perhaps the correct drivers are not installed and that can help you. If not check your logs and see if you are getting another error.

---

