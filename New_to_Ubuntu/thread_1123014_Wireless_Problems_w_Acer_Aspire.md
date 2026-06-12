---
title: "Wireless Problems w/ Acer Aspire"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by wgrosvenor64 on 2009-04-11
I installed Ubuntu 9.04 on my Acer Aspire 4720Z, as a dual boot w/ Windows Vista with no problem.  For some reason I lost my WLAN.  In order to get it back, I have to go into the terminal and type:

modprobe ath95k

Once I do this, my wireless works fine.  The only problem is, every time I reboot, I have to do the same thing over again.  What do I have to do in order for my wireless to be initiated upon boot up as opposed to me manually having to do it each time I boot?

---

### Post by llamabr on 2009-04-11
[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

---

### Post by ibuclaw on 2009-04-11
```
sudo gedit /etc/modules
```
And put in:
> ath5k
at the bottom of the file.


===============================================

Alternatively, you could have the module load immediately as you boot the computer:
```
sudo gedit /etc/initramfs-tools/modules
```
And put in:
> ath5k
at the bottom of the file. Then update your initramfs:
```
sudo update-initramfs -k all -u
```

Save and Quit, and upon reboot, your wireless should be working (with a sprinkle of hope ;)).

Regards
Iain

---

### Post by wgrosvenor64 on 2009-04-11
Thank you so much.  It worked out perfectly.


Code:

sudo gedit /etc/modules

And put in:
Quote:

ath5k

at the bottom of the file.

:guitar:

---

