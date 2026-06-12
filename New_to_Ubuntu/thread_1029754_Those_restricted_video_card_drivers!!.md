---
title: "Those restricted video card drivers!!"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by handrew on 2009-01-03
MSG deleted.   stale now..

---

### Post by Kareeser on 2009-01-03
Hm. The installation of drivers using EnvyNG is supposed to be painless. It's not a good sign that you can't get it installed.

Are there any error messages during the install?

---

### Post by 2hot6ft2 on 2009-01-03
> **Kareeser said:**
> Hm. The installation of drivers using EnvyNG is supposed to be painless. It's not a good sign that you can't get it installed.

Are there any error messages during the install?
Not always the case since envy will give you choices whether they work or not. Been there tried that and wasted about an hour in the process.

The best way to install graphics drivers is by using
System>Administration>Hardware Drivers
and choosing the one it recommends.

---

### Post by 2hot6ft2 on 2009-01-03
Found this maybe it will help since it fixed it for this user with the same card.
> Nvidia GeForce 7350LE
Go to synaptic and under repositories enable restricted software repository or some similar sounding name.

reload synaptic ( the button on far left).

now just search for nvidia-glx-new and install it.

Need a working internet connection as it will download from this newly enabled repository.
To break that down a bit more for you go to
System>Administration>Synaptic Package Manager
then settings, then repositories, then the Updates tab and mark the Unsupported Updates box then close then Refresh then search for nvidia-glx-new.

Mark it for installation and hit Apply

Once it finishes close synaptic and go back to
System>Administration>Hardware Drivers
and the driver should show up.

You can go back and uncheck the Unsupported Updates box if you want afterwards.

---

### Post by bobpur on 2009-01-03
You didn't say what version of Ubuntu you were using.

I have had more trouble with Ubuntu 8.10 and Linux Mint 6 (based on Ubuntu 8.10) as far as graphics drivers. 

The only install that was "painless" was with the Intel graphics on my Acer laptop.

Good luck.

---

### Post by handrew on 2009-01-04
Thansk for the replies boys.. But I've done all of that stuff and its a no-go. Interesting to note that one fellow is having the same trouble with his both ubuntu and mint. I currently am with ubuntu 8.10 and mint 6 and both are unable to install the nvidia driver. 
Also I installed the ubuntu 64 bit version and the nvidia driver installed perfectly. I prefer the 32 bit version as many software programs are not written for 64 bit yet, like Skype as an example. 

So I wonder if there is someone in the world that is specifically handling Nvidia drivers for ubuntu? (The GURU that is focused on video drivers)  Do you think the Company Nvidia may have a solution? After all they MUST HAVE tested their drivers on their cards with Ubuntu??? 

This is getting to me now. I've been at this for over 1 month and have read countless articles and tried many procedures with no results.

---

### Post by northern lights on 2009-01-04
The GeForce 7350 LE is supported by both the current 177 and the 173 driver versions. You can verify it [here]("http://us.download.nvidia.com/XFree86/Linux-x86/177.82/README/appendix-a.html"). I haven't checked for the other two legacy versions, but we don't care as we'll use 177 anyhow.

Open a terminal and run ```
sudo aptitude purge nvidia-173-kernel-source nvidia-173-modaliases nvidia-177-kernel-source nvidia-177-modaliases nvidia-71-kernel-source nvidia-71-modaliases nvidia-96-kernel-source nvidia-96-modaliases nvidia-cg-toolkit nvidia-common nvidia-glx nvidia-glx-173 nvidia-glx-173-dev nvidia-glx-177 nvidia-glx-177-dev nvidia-glx-71 nvidia-glx-71-dev nvidia-glx-96 nvidia-glx-96-dev nvidia-glx-dev nvidia-kernel-common nvidia-kernel-source nvidia-settings nvidia-xconfig && sudo apt-get clean && sudo apt-get autoremove
```to completely remove anything driver-related you could have possibly previously installed.

Subsequently, run```
sudo apt-get install nvidia-glx-177
```Reboot. You should be set.

---

