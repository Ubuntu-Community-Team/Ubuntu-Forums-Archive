---
title: "Video Card Woes"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by shade34321 on 2009-01-12
I have a Sapphire ATI X1650 Pro 512MB AGP video card. The other day when I booted up Ubuntu it displayed Cannot Display this Video Type. I've been using this card for about 2.5 months now and I've had Ubuntu installed for the past 2 months or so and it worked flawlessly!! I dual boot my computer with Windows XP pro and XP works just fine as do all of my games, except one which also gives me this error if I put the screen resolution to the default screen resolution of 1280x1024. I thought maybe the drivers were the problem and tried using a liveCD of Ubuntu to see if that would display and that wouldn't display either though it worked just a few weeks ago when I installed Ubuntu. I've submitted reports to both ATI and Sapphire and I'm currently waiting to hear back from them to see if they can help with this issue.

---

### Post by Svensk023 on 2009-01-12
what version of Ubuntu do you currently have installed?

---

### Post by Vince4Amy on 2009-01-12
Try installing the ATI Drivers as it appears that you have not yet done so. Here is my guide on how I install the drivers:

```
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-12-x86.x86_64.run
``` - Download The Driver

Run these:

```
sudo sh ati-driver-installer-8-12-x86.x86_64.run
``` - Run through the installer choosing the automatic steps

This Will Configure Xorg:

```
sudo aticonfig --initial -f
```

Reboot your system and everything should work, you can verify this with (run as normal user):

```
fglrxinfo
```

For a simple opengl test run:

```
glxgears
```

---

### Post by shade34321 on 2009-01-12
I have Ubuntu 8.10 and I have installed the ATI drivers for the card. I'm sorry I had forgotten to mention it before. Also I'm not able to do anything with the OS because I'm unable to see anything. Once it gets past the loading screen, when I'm supposed to log in, I can no longer see anything besides that message on a black background.

---

### Post by Vince4Amy on 2009-01-12
> **shade34321 said:**
> I have Ubuntu 8.10 and I have installed the ATI drivers for the card. I'm sorry I had forgotten to mention it before. Also I'm not able to do anything with the OS because I'm unable to see anything. Once it gets past the loading screen, when I'm supposed to log in, I can no longer see anything besides that message on a black background.

Where did you install the ATI drivers from? ATI Website, Restricted manager or envy-ng?

---

### Post by shade34321 on 2009-01-12
I believe it was the restricted drivers Ubuntu told I could install. Sorry I can't remember off the top of my head where it was at so I'll try and describe it as best as I can. After installing I got a notice at the top saying I could use restricted drivers for my video card. Upon clicking the notice it brought up a box which allowed me to install these drivers.

---

### Post by shade34321 on 2009-01-14
So yesterday i accidentally booted into Ubuntu and it worked. Not sure what the problem was but now it's working.

---

