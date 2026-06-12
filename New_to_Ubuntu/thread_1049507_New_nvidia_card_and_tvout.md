---
title: "New nvidia card and tvout"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by mikwig on 2009-01-24
Have been using an onboard intel card for a while with no problems, but wanted to watch DVD's on tv through my ubuntu box - we bought an Nvidia 8400 card cause from what I have seen on the forums nvidia is fairly well supported.

The problem:

If the tv and the monitor are connected at the same time then the TV is detected as the primary display from power on - is this normal?

it is making configuring a nightmare.

---

### Post by diablo75 on 2009-01-24
Try this:

Click Applications>Accessories>Terminal

Type in:

```
sudo apt-get install nvidia-settings
```

Once that is done type:

```
sudo nvidia-settings
```

You'll be able to modify your display configuration and then save it to your xorg.conf with the save button at the bottom.

---

### Post by mikwig on 2009-01-24
Thankyou for the quick reply.

The dilemma is that it goes into low-res/unreadable mode if the tv is the main screen, and if the TV is connected then nvidia-settings won't detect it if it isn't plugged-in.

update - 

after fiddling with nvidia-settings for a while I managed to get the computer to boot through the TV (which is only black and white) whilst gdm will start on the monitor. The TV is gone again and I am left with one X screen. Nvidia-settings is still saying that my TV is disabled.

---

