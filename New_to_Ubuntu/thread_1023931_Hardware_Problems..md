---
title: "Hardware Problems."
date: 2008-12-28
forum: New to Ubuntu
---

### Post by ShadowfoxXXX on 2008-12-28
I have a toshiba satellitle l35-s1054.
My laptop speakers do not have any output, but headphones work.
My webcam is a Microsoft Lifecam vx3000. Easycam recognizes and installs it, but every other program won't work with it.
My graphics card is an ATI radeon xpress 200m. I cannot adjust the brightness with the applet, but the brightness keys on my laptop work.

Somebody please help, as i want to switch completely to ubuntru but i can't because of this.

---

### Post by ShadowfoxXXX on 2008-12-28
bump

---

### Post by linux_tech on 2008-12-28
If you are familiar with using alsamixer, this command will will show all the alsamixer settings


Code:

```
alsamixer -D hw:0
```

you can also use Gnome-alsamixer, but you will need to install it first.


```
sudo apt-get install gnome-alsamixer
```

Then to open gnome-alsamixer type

```
gnome-alsamixer
```

check all settings, make sure nothing is muted, volume is up;
make sure front,master is checked, try unchecking headphones

---

### Post by ShadowfoxXXX on 2008-12-28
thx so much. figured it out, well the speakers. still ahve the problem with the webcam and the screen

---

### Post by ShadowfoxXXX on 2008-12-28
Bump

---

### Post by ShadowfoxXXX on 2008-12-28
huh..... bump.

---

