---
title: "I can't use bluetooth and wifi simultaneously-rtl8723de"
date: 2019-09-05
forum: Networking &amp; Wireless
---

### Post by daniel4128 on 2019-09-05
I have an HP laptop running Ubuntu 19.04. I'm unable to simultaneously use bluetooth and wifi. Anytime i try to connect to the wifi while I'm using bluetooth audio, the audio starts getting distorted. It gets better when I disconnect from the wifi. This doesn't happen in Windows. My PC uses the rtl8723de driver. Any help? Thanks.

---

### Post by cruzer001 on 2019-09-05
Blueman worked out of the box on my HP Elite.
```
sudo apt install blueman
```
Maybe you will be so lucky :)

---

### Post by daniel4128 on 2019-09-06
> **cruzer001 said:**
> Blueman worked out of the box on my HP Elite.
```
sudo apt install blueman
```
Maybe you will be so lucky :)

Tried it. Unfortunately, I'm still getting the same result. Thanks for the help though.

---

### Post by cruzer001 on 2019-09-06
bluez bluez-tools rfkill

Got those installed?  I was looking at this:
[https://www.maketecheasier.com/setup-bluetooth-in-linux/](https://www.maketecheasier.com/setup-bluetooth-in-linux/)

other hits that could help
[https://askubuntu.com/questions/1078847/how-to-set-up-bluetooth-in-ubuntu-18-04](https://askubuntu.com/questions/1078847/how-to-set-up-bluetooth-in-ubuntu-18-04)

[https://ubuntuforums.org/showthread.php?t=2387182](https://ubuntuforums.org/showthread.php?t=2387182)

I have not had to troubleshoot bluetooth to any great degree, my help is limited.

---

