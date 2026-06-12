---
title: "booting ubuntu problem"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by kartik3958 on 2009-12-14
I have installed windows7 than ubuntu desktop 9.10 64 bit than ubuntu server 9.10 and than I have installed opensuse 11.2 but after installing opensuse I find the choice of windows and opensuse for booting there were no choice for ubuntu and ubuntu server please solve my problem.

---

### Post by talsemgeest on 2009-12-14
Run through the instructions here: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Once you can boot into ubuntu, run this from a terminal: ```
sudo update-grub
``` This should search your hard drives for OSs, and add them to your boot list.

---

### Post by kartik3958 on 2009-12-15
after doing so I have loss my choice of opensuse booting.

---

