---
title: "need help for web cam"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by Geek-abor on 2010-12-06
i have installed ubuntu 10.10 with Wubi and started to use ubuntu and i thing in future i'm gonna use only ubuntu but i can't use my webcam (Logitech Fusion quickcam,looks like this [http://pan3.fotovista.com/dev/3/2/02070023/l_02070023.jpg](http://pan3.fotovista.com/dev/3/2/02070023/l_02070023.jpg)) on skype and emesene.i have tried gstreamer-properties and i can see something on gstreamer but when i start it on skype it's just black

---

### Post by UltraMathMan on 2010-12-06
From what I've found after some light Googling, it might be an issue with the video kernel module for the camera loading before the audio kernel module. You can check the system log with ```
cat /var/log/syslog | grep uvcvideo 
``` If you see something like > newcompy kernel: [  881.672050] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -110 (exp. 26).
May 17 11:40:47 newcompy kernel: [  882.672039] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -110 (exp. 26).
May 17 11:40:47 newcompy kernel: [  882.672042] uvcvideo: Failed to initialize the device (-5). Try reloading the video kernel module using ```
sudo rmmod uvcvideo && sudo modprobe uvcvideo
```

Hope this helps :)

Source: [http://indiangeek.com/blog/?p=60]("http://indiangeek.com/blog/?p=60")

---

### Post by Geek-abor on 2010-12-06
it looks like it worked
emesene still to test :D
thank you

---

### Post by Geek-abor on 2010-12-06
i have another problem with ubuntu and don't wanna open a lot of threads
my problem is that any text (menu,panels,etc.) becomes after a while unreadable like in this pic

---

### Post by baddnady23 on 2010-12-06
> **Geek-abor said:**
> i have another problem with ubuntu and don't wanna open a lot of threads
my problem is that any text (menu,panels,etc.) becomes after a while unreadable like in this pic

This is a whole new issue and is best opened in a new thread for the best response.

---

