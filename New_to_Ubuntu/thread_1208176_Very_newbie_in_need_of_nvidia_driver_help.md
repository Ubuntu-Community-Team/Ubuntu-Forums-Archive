---
title: "Very newbie in need of nvidia driver help"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by Corbinator on 2009-07-08
Hello all, I am very new to Linux, I am trying to install an Nvidia driver for my GeForce 9400gt in a new build. I am using 8.04, and am getting and error stating that "you appear to be running an X Server; please exit before installing." The next screen states "Please see the file '/var/log/nvidia-installer.log' for details." How do I do this and what is wrong. I am slightly tech-savy but it's mostly in dos language. Any assistance will be greatly appreciated as I am stuck in 800x600 res. I have tried Envyng and it also couldn't find a driver to support my video card. Also how do I exit the full terminal without rebooting?

---

### Post by mano cazalet on 2009-07-08
how exactly you tried to install the drivers?

in system--» administration--»hardware dirvers there should be an option to activate your drivers

---

### Post by mikewhatever on 2009-07-09
The 'xserver running' error means just that. You have to stop it with the following command, after saving all unfinished work, **sudo /etc/init.d/gdm stop** or use the recovery mode, in which case, xserver isn't started in the first place.

System->Admin->Hardware Drivers would have been a good option, had you been running Jaunty. I think the nvidia driver provided for Hardy is too old for you card.

---

### Post by 3rdalbum on 2009-07-09
Why are you using Ubuntu 8.04 on what is presumably a very recent consumer-level computer? It's over a year old; try Ubuntu 9.04 and your graphics card driver will be available in the Hardware Drivers program.

---

### Post by duanedesign on 2009-07-09
I do not have your particular card however I do have an NVIDIA card and have installed drivers from this repository successfully. A fellow Forum user with your exact card installed the 180.** driver from this repository and it works great for him.

Add the signing GPG key

```
wget http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key && sudo apt-key add ubuntu-repos.key && rm ubuntu-repos.key
```

Add the repository

```
echo "deb http://www.avenard.org/files/ubuntu-repos hardy release" | sudo tee /etc/apt/sources.list.d/avenard.list
```

Now **open** Synaptic Package Manager.

System-> Administration-> Synaptic Package Manager

In the Quick Search at the top of the Manager type in:

**nvidia-glx-180**

click the box to the left of the package name and select install.
It should also install two other packages.
[B]nvidia-180-kernel-source
nvidia-180-libvdpau[/B]

*OPTIONAL:* also I would recommend you install nvidia-180-modaliases

After you make your selections hit **Apply**.

Now **Reboot**.

Hope this helps.

---

### Post by Corbinator on 2009-07-09
Thanks all but none of it worked. It recognizes my monitor now but I'm stuck in 640X480, but I have a refresh rate of 75 Hz. I was using Hardy because it was already installed on a hard drive I have. I think I'm just going to upgrade to 9.04 hopefully that will work.

---

### Post by Garyhans on 2009-07-09
The only problem I've had with Nvidia is using xserver with to monitors.. since the upgrade to Jaunty.. and the Nvidia-Settings In the reg menu.. isn't done with gksudo..  and doesn't stick..

---

### Post by zerhacke on 2009-07-09
I've found that since Ubuntu started using a smart xorg.conf file many, many, many monitors are not supported very well.

If you have the ability, I suggest trying another monitor. All you have to do is shut down, unplug the monitor you have, plug in a different monitor, and restart.

---

### Post by Corbinator on 2009-07-13
Thank you all, I have upgraded to Jaunty and everything is smooth sailing!!! I have the same problem with the dual monitor thing but it did recognise both my monitors. I appreciate all the help and will be back with more questions I am sure as I move along with my complete boycot of Windows. DOWN WITH MICROSOFT!!!!

---

