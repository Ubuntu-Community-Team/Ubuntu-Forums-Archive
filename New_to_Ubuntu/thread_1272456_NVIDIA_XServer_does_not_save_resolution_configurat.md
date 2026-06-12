---
title: "NVIDIA XServer does not save resolution configurations"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by SriLankanBoy on 2009-09-22
I recently installed the NVIDIA driver 185.xxxx from another guide from Ubuntuforums located at 

```
http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+185
```

I switched to widescreen (16:9) recently. Now ubuntu always loads with the previous 1024x768 resolution. When I change it to 1280x720 and again shutdown or log off and come back, it again loads to the 1024x768. When I try to save the configuration it shows the below error.

[IMG]http://i33.tinypic.com/5ko7kz.jpg[/IMG]


Before that I was using a standard 4:3 LCD. That time also, I faced this same problem. That time I used this shortcut (Got it from another site).

```
xrandr --output VGA --mode 1024×768 --rate 75
```

How can I set my default resolution to 1280x720 again ? :confused:

Help much appreciated ! :)

---

### Post by JillSwift on 2009-09-22
To write to the xorg.conf files you need to run that as root.

in a terminal:
```
gksudo nvidia-settings
```

---

### Post by SriLankanBoy on 2009-09-29
Thanks. It worked ! :)

I love Ubuntu ... :guitar:

---

