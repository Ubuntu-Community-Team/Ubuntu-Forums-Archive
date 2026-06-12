---
title: "desktop computer boots into text mode after nvidia drivers installed"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by FraggerMan on 2011-01-12
Hey guys, sort of a noob to ubuntu here, but not a noob to general computing. After installing ubuntu 64 bit, I installed all my updates and installed the current nvidia driver for my 9800 GTX+ from the additional drivers page. After restarting my computer, ubuntu boots into text mode. I used google and found out a couple of commands like 

sudo dpkg -reconfigure -phigh xserver-xorg - does nothing
after i hit control+alt+f7 it hangs on checking battery state with NO ok to the right of it.
after running sudo apt-get --purge remove nvidia -current and restarting the computer,
the boot hangs on the ubuntu screen everytime.

Thanks for reading guys, and any or all help would be highly appreciated.

My specs are:
Core i7 860
4 GB of ram
Nvidia 9800 GTX+

---

### Post by FraggerMan on 2011-01-12
bump this! need help please!

---

### Post by 3602 on 2011-01-12
You should be able to boot into Recovery Grub and start failsafe-X, then from there you can disable the proprietary nVidia driver... But I don't know the details. When your computer you can furiously press Shift repeatedly to get into the Grub menu, then you choose a Recovery Mode kernel. But I don't know how to get into failsafe-X... Sorry.

---

### Post by FraggerMan on 2011-01-12
Thanks anyway.

---

### Post by shreepads on 2011-01-13
Which version of Ubuntu are you using and when you say 'installed the current nvidia driver' did you install the proprietary drivers from the System > Administration > Hardware Drivers option or the latest ones downloaded from the NVidia site?

Restart, choose the recovery mode option and then choose the 'root shell with networking' option in the next list presented.

Please check if there is a /etc/X11/xorg.conf file

```
ls /etc/X11/xorg*
```

And if the nouveau or nvidia drivers are loaded

```
modprobe -l | grep nouveau
modprobe -l | grep nvidia
```

Any time you want to shutdown use

```
init 0
```

---

### Post by FraggerMan on 2011-01-13
I'm running 10.10 64 bit and i installed them from the additional drivers page.

---

### Post by FraggerMan on 2011-01-13
bump

---

### Post by shreepads on 2011-01-14
I think we're in different timezones so some delay is probably expected...

Please run the commands listed in my previous note from the root shell (basically a text-only mode, with a prompt that starts with "root"; details for getting to this are also in my post) and post the response from them. If you have any problems while doing this, post that as well...

And while you're at it, run this from the root shell as well and post the output:

```
cd /etc/modprobe.d
cat * | grep nouveau
```

---

### Post by FraggerMan on 2011-01-14
Nothing happens when I write those commands. After I went to that directory in terminal, and ran that command, nothing happened.

---

### Post by fraser_m on 2011-01-14
When you reboot, does the screen flicker a couple of times before dropping to text mode?

---

### Post by fraser_m on 2011-01-14
When you reboot, does the screen flicker a few times before dropping to text mode?

---

### Post by FraggerMan on 2011-01-15
No, It shows a ubuntu 10.10 screen but no graphics and then it goes to text mode.

---

### Post by FraggerMan on 2011-01-15
No it does not, it shows a ubuntu 10.10 screen that looks un graphical.

---

### Post by FraggerMan on 2011-01-16
bump guys

---

### Post by Splat_NJ on 2011-01-16
For help look [here]("https://help.ubuntu.com/community/Video") and [here.]("http://ubuntuforums.org/showthread.php?t=1467074")

---

### Post by shreepads on 2011-01-17
> **FraggerMan said:**
> Nothing happens when I write those commands. After I went to that directory in terminal, and ran that command, nothing happened.

OK, what that means is
- There is no /etc/X11/xconf.org file, i.e. the system should autodetect and configure X
- None of the nouveau or nvidia drivers are running, which probably explains why you can't get a graphical interface
- The default nouveau drivers are not blacklisted in modprobe.d, which PROBABLY means they are not installed

Boot into the Recovery Mode > Root Shell with Networking and try this. This is a recipe picked up from here:

[https://wiki.edubuntu.org/X/Troubleshooting/NvidiaDriverSwitching#Problem:%20%20Need%20to%20fully%20remove%20-nvidia%20and%20installing%20or%20reinstall%20-nouveau%20from%20scratch](https://wiki.edubuntu.org/X/Troubleshooting/NvidiaDriverSwitching#Problem:%20%20Need%20to%20fully%20remove%20-nvidia%20and%20installing%20or%20reinstall%20-nouveau%20from%20scratch)

```
sudo nvidia-settings --uninstall
  sudo apt-get remove --purge nvidia*
  sudo apt-get remove --purge xserver-xorg-video-nv xserver-xorg-video-nouveau
  sudo apt-get install nvidia-common
  sudo apt-get install xserver-xorg-video-nouveau
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
```

Some of the steps will produce errors (e.g. you have already uninstalled nvidia*) but just go ahead.

Following this you should be able to do a normal boot into a basic graphical interface.

Now please try this to install the latest NVidia drivers from the NVidia site. This SHOULD fix it...

[http://ubuntuforums.org/showthread.php?t=1665630](http://ubuntuforums.org/showthread.php?t=1665630)

---

### Post by FraggerMan on 2011-01-17
> **shreepads said:**
> OK, what that means is
- There is no /etc/X11/xconf.org file, i.e. the system should autodetect and configure X
- None of the nouveau or nvidia drivers are running, which probably explains why you can't get a graphical interface
- The default nouveau drivers are not blacklisted in modprobe.d, which PROBABLY means they are not installed

Boot into the Recovery Mode > Root Shell with Networking and try this. This is a recipe picked up from here:

[https://wiki.edubuntu.org/X/Troubleshooting/NvidiaDriverSwitching#Problem:%20%20Need%20to%20fully%20remove%20-nvidia%20and%20installing%20or%20reinstall%20-nouveau%20from%20scratch](https://wiki.edubuntu.org/X/Troubleshooting/NvidiaDriverSwitching#Problem:%20%20Need%20to%20fully%20remove%20-nvidia%20and%20installing%20or%20reinstall%20-nouveau%20from%20scratch)

```
sudo nvidia-settings --uninstall
  sudo apt-get remove --purge nvidia*
  sudo apt-get remove --purge xserver-xorg-video-nv xserver-xorg-video-nouveau
  sudo apt-get install nvidia-common
  sudo apt-get install xserver-xorg-video-nouveau
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
```

Some of the steps will produce errors (e.g. you have already uninstalled nvidia*) but just go ahead.

Following this you should be able to do a normal boot into a basic graphical interface.

Now please try this to install the latest NVidia drivers from the NVidia site. This SHOULD fix it...

[http://ubuntuforums.org/showthread.php?t=1665630](http://ubuntuforums.org/showthread.php?t=1665630)

Running these commands leaves me an error at libg11-mesa-g1x and libg11-mesa-dri not found and the reconfiguring command does nothing again. I can boot ubuntu but im left at a stuck ubuntu load page with the dots not moving.

---

### Post by shreepads on 2011-01-18
> **FraggerMan said:**
> Running these commands leaves me an error at libg11-mesa-g1x and libg11-mesa-dri not found and the reconfiguring command does nothing again. I can boot ubuntu but im left at a stuck ubuntu load page with the dots not moving.

Stupid question, are you sure you're typing them in right?

In your post above you've mentioned 

'libg11-mesa-g1x and libg11-mesa-dri', 

but the names are actually

'libgl1-mesa-glx libgl1-mesa-dri', 

or in allcaps

'LIBGL1-MESA-GLX LIBGL1-MESA-DRI'
(don't use the allcaps version)

---

### Post by FraggerMan on 2011-01-18
> **shreepads said:**
> Stupid question, are you sure you're typing them in right?

In your post above you've mentioned 

'libg11-mesa-g1x and libg11-mesa-dri', 

but the names are actually

'libgl1-mesa-glx libgl1-mesa-dri', 

or in allcaps

'LIBGL1-MESA-GLX LIBGL1-MESA-DRI'
(don't use the allcaps version)

Wouldn't it be smarter to reinstall ubuntu and run the instructions from here [http://ubuntuforums.org/showthread.php?t=1665630](http://ubuntuforums.org/showthread.php?t=1665630)

---

### Post by shreepads on 2011-01-19
Well yes, but only if this is a relatively fresh install which hasn't seen much use so far. 

Pragmatically you could do this even if this is a fairly used install but I try to avoid that as it sort of defeats the purpose of using Ubuntu... Seems a lot like the old Windows' "reinstall to fix" method...

If you decide to take this approach I would suggest doing a fresh install using the Ubuntu 10.04.1 Lucid Lynx LTS (Long Term Support) version. 32-bit if you have less than 4 GB of RAM (the core OS is pretty solid in 64-bit but not all app devs have caught up).

URL:
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

Unless, of course, there is something specific in 10.10 that you need...

---

