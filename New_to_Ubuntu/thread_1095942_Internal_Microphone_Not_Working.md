---
title: "Internal Microphone Not Working"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by Linux000 on 2009-03-14
My internal microphone on my Dell Latitude D830 is not working. I have Ubuntu 8.10 Intrepid Ibex. My speakers work, but my microphone has never worked, I have tried changing the device under System/Administration/Sound, and can not find a device that fits my speakers and microphone.

---

### Post by Troll_the_Great on 2009-03-14
Hy. I have an ASUS laptop and had the same problem as you. I fixed it with the following commands:

```
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
```

Hope it works for you too.
Cheers!

---

### Post by Linux000 on 2009-03-15
Looking at it real fast, I notice you are using the ALSA drivers my system is set up with a OSS card, and trying it out, it dosen't work.

---

### Post by Linux000 on 2009-03-16
Tried it again, says Build of the ALSA source failed.

---

### Post by Linux000 on 2009-03-16
Found the solution after googleing around:D figured I would post it here, fix for 8.04, but it works in Ibex (8.10)

[http://ubuntuforums.org/archive/index.php/t-786912.html](http://ubuntuforums.org/archive/index.php/t-786912.html)

thanks to all

---

