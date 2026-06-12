---
title: "Acer crystal eye on 9.04"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by sgd1977 on 2009-10-08
Hello,

I'm trying to get the Crystal Eye webcam on my Aspire 4530 to work. Ubuntu recognises it as Acer Crytal Eye Webcam but I'm not able to get it to work. I've tried this using Cheese and Skype. Neither of them show any output.

Please help! Almost every other hardware component is working in my setup except this.

I've gone through past threads on this and tried other Webcam tools as well but have not been able to resolve the problem. Should I try to download some specific package to get this to work?

BTW, on Vista, the webcam works without any driver (or some Windows default driver) installed.

---

### Post by LewRockwell on 2009-10-08
In a few days you'll be able to try out Ubuntu 9.10 Karmic Koala and see how it performs on your equipment

Til then it's probably not worth your time to mess with it

otherwise, something like this might give you some ideas:

[http://ubuntuforums.org/showthread.php?t=1005416](http://ubuntuforums.org/showthread.php?t=1005416)

.

---

### Post by itaBannet on 2009-10-08
> **sgd1977 said:**
> Hello,

I'm trying to get the Crystal Eye webcam on my Aspire 4530 to work. Ubuntu recognises it as Acer Crytal Eye Webcam but I'm not able to get it to work. I've tried this using Cheese and Skype. Neither of them show any output.

Please help! Almost every other hardware component is working in my setup except this.

I've gone through past threads on this and tried other Webcam tools as well but have not been able to resolve the problem. Should I try to download some specific package to get this to work?

BTW, on Vista, the webcam works without any driver (or some Windows default driver) installed.

same problem but on an acer 5920G.
how can i see which drivers is now using the webcam? :confused:

---

### Post by itaBannet on 2009-10-08
ok, webcam is currently working with aMSN but not with Skype.
why?

---

### Post by sgd1977 on 2009-10-09
> **LewRockwell said:**
> In a few days you'll be able to try out Ubuntu 9.10 Karmic Koala and see how it performs on your equipment

Til then it's probably not worth your time to mess with it

otherwise, something like this might give you some ideas:

[http://ubuntuforums.org/showthread.php?t=1005416](http://ubuntuforums.org/showthread.php?t=1005416)

.

Thanks Lew.

Couple of things:
1) I have been able to get the camera to work. Don't ask me how. I learnt a lot of new things about working with webcam. On Windows I just had to stare at it. On Ubuntu, I've discovered cheese, luvcview, a couple of diagnostic commands: lsusb, lsmod, dmesg, modprobe, etc that I didn't know of before. Finally, after a number of reboots something went right and the camera sputtered to life on cheese and luvcview. Like an old car that needs a bit of encouragement to get going :-)

2) Yeah, I'm looking forward to trying this on 9.10. Webcam was the last piece of crucial hardware I needed to get working to seriously consider migrating to Linux. I'm hoping with 9.10 I won't have to do as much R&D. The various diagnostic commands I tried clearly recognise the device as Crystal Web Cam down to the minor revision number.

---

