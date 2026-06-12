---
title: "Black screen on start-up"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by Nigters on 2011-04-14
I've had the 11.04 beta running for a few days and it's been running fine until last night.

I was trying to get my second display to work with Ubuntu and changed a few settings in the nvidia x driver options and saved them to some configuration file. I think it was called x-server or something.

When I log in to Ubuntu the second screen turns on as in it's getting something telling it to turn on, which it wasn't doing before, but the screen just stays black and theres no login sound etc.

How do I fix this? 
I could just wait until 11.04 is fully released I guess, since I don't need Ubuntu, it was more for fun that I installed it.

---

### Post by TeoBigusGeekus on 2011-04-14
Boot up to recovery mode from grub and, once in terminal, delete your xorg.conf file
```
sudo rm /etc/X11/xorg.conf
```
Reboot
```
sudo reboot
```
and you should be able to reach your desktop.

---

### Post by Nigters on 2011-04-14
I will try that as soon as I can.

Is there a correct procedure to getting my secondary display to work with the nvidia drivers then?

---

### Post by TeoBigusGeekus on 2011-04-14
Once on your desktop, open a terminal and give
```
gksu nvidia-settings
```
Do your configuration from there. When, done, don't forget to check the "Save to X configuration file" button.
Reboot. Cross your fingers.
If it works, well done.
If not, delete the xorg.conf file and start again.

---

### Post by Nigters on 2011-04-14
The command did not work, it said something alone the lines of "Could not remove xxx, no such file or directory exists"

---

### Post by TeoBigusGeekus on 2011-04-14
Can you post the exact command you used?
Press the up arrow in terminal and it will show up.

---

### Post by Nigters on 2011-04-14
It would appear that the x in X11 needed to be capitalized, it worked the second time :)

I shall try configuring it properly now, thanks for your help!

---

### Post by TeoBigusGeekus on 2011-04-14
I hope that you'll get it fixed.

---

