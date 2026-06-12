---
title: "how do I reinstall drivers for video card?"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by ThePinkWitch on 2010-02-24
hello :) I had the drivers that Ubuntu put in for my graphics card working fine but I was looking through the software package manager and saw ati catalyst control centre in the packages and thought it would be good to install that. For some reason after I did I couldn't enable desktop effects or emerald and my AWN is all messed up. I uninstalled the Ati but I still can't enable desktop effects or emerald :( How do I get the drivers back that came already installed with ubuntu? Thanks for any help. I wish I would stop messing with stuff that aint broke :D

---

### Post by mikewhatever on 2010-02-25
The driver you want is probably xserver-xorg-video-ati, but I doubt it needs reinstalling. Try booting in recovery mode and selecting fixX option.

---

### Post by 3rdalbum on 2010-02-25
If your graphics were working out-of-the-box on Ubuntu, then you might need to remove all packages that have "fglrx" in their name. The ATI control center only works if you have ATI's official driver, and their official driver doesn't work with all their graphics cards. So when you installed the control center, Ubuntu would have also installed the ATI driver, which is called "fglrx".

---

### Post by ThePinkWitch on 2010-02-25
> **mikewhatever said:**
> The driver you want is probably xserver-xorg-video-ati, but I doubt it needs reinstalling. Try booting in recovery mode and selecting fixX option.

I restarted in recovery but couldn't find anything about fixX so I got it to repair all packages to see if that would help and had a few panicky moments trying to get out of there because it would just go to terminal and I didn't know how to get out lol just restarted in the end :p

---

### Post by ThePinkWitch on 2010-02-25
> **3rdalbum said:**
> If your graphics were working out-of-the-box on Ubuntu, then you might need to remove all packages that have "fglrx" in their name. The ATI control center only works if you have ATI's official driver, and their official driver doesn't work with all their graphics cards. So when you installed the control center, Ubuntu would have also installed the ATI driver, which is called "fglrx".

This worked. I did that, then went to visual effects and clicked on custom effects and it reinstalled the previous driver. Working great now. THANKYOU BOTH OF YOU! :)

---

### Post by mikewhatever on 2010-02-25
It was xfix, instead of fixx, I guess that's what confused you.:)

[http://www.psychocats.net/ubuntu/images/resetpassword03.png](http://www.psychocats.net/ubuntu/images/resetpassword03.png)

---

