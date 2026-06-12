---
title: "lm-sensors help"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by mvalviar on 2010-02-06
I just installed lm-sensors but I can't detect any sensors. Here's what I get with sudo sensors-detect```
Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See
http://www.lm-sensors.org/wiki/FAQ/Chapter3 for further information.
If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.

```
I visited that URI but it's all greek to me. Heres what I know my current motherboard is an Asus p5kpl-am se. lm-sensors used to work on my old motherboard. I forgot what model it was. I've read that the repo version of lm-sensors doesn't work. I tried to compile from source but it's not working as well.

I there a way for me to fix this? I need to monitor my cpu temp. I can already see that my cpu fan is already dusty.

---

### Post by mvalviar on 2010-02-06
up

---

### Post by marco.tonoli@libero.it on 2010-02-27
i have same problem on same mb, 9.04.

can someone help ?

thanks

---

### Post by GSF1200S on 2010-02-27
Try going to the lm_sensors homepage and download the latest beta version:
[http://www.lm-sensors.org](http://www.lm-sensors.org)

You should remove the current repo version of lm_sensors:
```
sudo apt-get remove lm-sensors
```

You will also need some build dependencies:
```
sudo apt-get install build-essential
```

You then unpack the source you downloaded into a directory and change into it with a terminal. So, lets say your username is user, and you extracted (using the archive manager when you right click on the package/tarball) the source to a directory on your desktop. In the terminal, you would do:
```
cd ~/Desktop
```

The you run:
```
./configure
```
```
sudo make
```
```
sudo make install
```

If it complains that ./configure doesnt exist, skip that step and just run the make commands (i cant check as it seems the page is currently down). If at any point you run into errors, try running:
```
sudo make clean
```
and then run the command you received errors from again. If you still have errors, copy the terminal results and paste them here.

This is what I had to do to get sensors working on my i7 desktop- the repo version will not detect any sensors. Good luck :)

---

### Post by urosg3 on 2010-02-27
I have same MB and working LM-sensors out of box. Strange...

---

