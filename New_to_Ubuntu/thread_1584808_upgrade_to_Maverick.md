---
title: "upgrade to Maverick"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by beew on 2010-09-29
I got an (free :))old laptop so I could do some experiments on it. It has a Nvidia Gforce4 graphic card. I installed Lucid on it with the live usb, activated the Nvidia drivers using "hardware driver" and rebooted, everything was easy and smooth enough. I then thought maybe I should upgrade it to Maverick. 

So I did and it took several hours. But there was no graphic, I booted right into a terminal. I thought may be the Nvidia driver was removed during the upgrade and nothing was installed to replace it. But it didn't matter because it was just a trial run so I reinstalled Lucid but this time did the upgrade without installing the Nvidia driver.

It took another 4-5 hours for the upgrade and I got Maverick.  Now I wanted to install the Nvidia driver.

First, "hardware driver" (or whatever it is called in Maverick) didn't detect the Nvidia driver (a bug?)

It didn't matter since I know the package, so I installed it from Synaptic and rebooted. After reboot the graphic has markedly improved but strangely when I tried to fix the resolution the Nvidia graphic manager (I don't know what it is called) showed up and said that the Nvidia card needs to be activated ( I thought it was already activated seeing that the display was much better) so I ran in the terminal ```
sudo nvidia-xconfig
```and rebooted. 

This time I have no more graphic but instead booted into a terminal. I ran "startx" and was told that there was no screen. I wonder what is going on.
[B]
Edited:[/B] Sorry, can't take screen shots or produce error logs from that computer right now. All I see is  a flashing command prompt.. (in other words, the ideal desktop for some command line jocks here. :))

---

### Post by beew on 2010-09-29
Ok, I got these error messages while trying to run startx

> failed to load /usr/lib/xorg/extra-modules/nvidia-drv.so

failed to load module "nvidia" (loader failed, 7)

fatal server error: 
no screen found

xint: no such file or directory (errno 2)
xint: no such process (errno3)
xauth: error in locking authority file /home/username/.xauthority

Thanks in advance for any help.

---

### Post by jtarin on 2010-09-29
[There's this]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")....[And this.]("https://bugs.launchpad.net/ubuntu/maverick/+source/nvidia-graphics-drivers/+bug/616023")

---

### Post by beew on 2010-09-29
> **jtarin said:**
> [There's this]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")....[And this.]("https://bugs.launchpad.net/ubuntu/maverick/+source/nvidia-graphics-drivers/+bug/616023")

Hi, thanks. The launchpad link doesn't help, I am not using drivers in 2.56.53. The package only works for newer Nvidia cards (> 6, I have a 4). So bug fixes in that package do me no good.

But anyway it seems that I have finally screwed up in such a way that I have to do a clean install (and I know for sure that Lucid works)

From the terminal I purged the nvidia packages. Now when I reboot I am stuck with the purple splash screen with "Ubuntu" and 5 orange dots, I can't even get into the terminal anymore. :-k

---

### Post by mocoloco on 2010-09-29
Honestly I don't know if it's worth the trouble, Maverick is still beta and the upgrade process isn't as smooth as it should be either. If you really want Maverick now maybe try re-installing from the [Maverick daily build]("http://cdimage.ubuntu.com/daily-live/current/").

---

