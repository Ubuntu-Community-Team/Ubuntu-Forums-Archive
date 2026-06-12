---
title: "Questions"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by Teyphas on 2009-09-06
Hello everyone! I'm just another noob, installed Linux :D I know...maybe you tired of all these questions, but I'll try.
I've installed Ubuntu 9.04 in Windows. This thing is fast :D I like it very much.

I have 19" monitor, 1366x768 screen resolution. On Ubuntu i have 800x600 only. So..How can i add proper screen resolution?

I've watched many times how beatiful visual effects are. It's maybe another reason why i've installed Ubuntu :KS But...i can't enable it. I have GeForce 9400-if it will help somehow...

And is it possible to work with Wacom Intuos4 graphic tablet in Ubuntu?

That's all...for now:D

P.S: Sorry if i made some mistakes in English. I'm not perfect english speaking person, but i think you'll understand me.

Thanks.

---

### Post by scragar on 2009-09-06
First do a check for restricted drivers in the system menu(Can't remember where it is exactly), if not you may want to try envy.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
First, enable the universe repository, it's not that hard if you follow the graphical instructions in section 2.
Then install Envy from there:
```
sudo apt-get update
sudo apt-get install envyng-qt
```
Then launch envy from applications>system tools.

This will update your graphics driver to the official restricted driver(from the generic driver you are likely using).

---

### Post by TeoBigusGeekus on 2009-09-06
System->Administration->Hardware Drivers
Activate the proper driver an then enable Desktop effects.

---

### Post by Favux on 2009-09-06
Hi Teyphas,

Yes you can set up the Intuos4 in Jaunty.  See post #176:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

---

### Post by ikisham on 2009-09-06
When you activate the nvidia driver (which you may have done by now since it prompts by itself a notification) you may have the proper resolution.
For effects, check System > Preferences > Appearance > Effects, check 'extra' and install 'compizconfig-settings-manager' for all the settings options:
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by Teyphas on 2009-09-06
Thanks for answers. Ok. I went to hardware drivers...but the list is empty:(, so i can't enable anything:D

---

### Post by halitech on 2009-09-06
follow the instructions and download here:

Installation instructions: Once you have downloaded the driver, change to the directory containing the driver package and install the driver by running, as root, sh ./NVIDIA-Linux-x86-185.18.36-pkg2.run (sudo sh ./NVIDIA-Linux-x86-185.18.36-pkg2.run)

[http://www.nvidia.com/object/linux_display_amd64_185.18.36.html](http://www.nvidia.com/object/linux_display_amd64_185.18.36.html)

---

