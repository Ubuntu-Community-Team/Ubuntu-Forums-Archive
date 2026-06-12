---
title: "Nvidia 560 driver install help"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by rklapp on 2011-04-26
Could someone please point me in the right direction (or walk me through) for fixing my nvidai driver? I have a 560ti and noticed that nvidia has certified drivers. I used the website's instructions and now I'm stuck in the failsafe low-res graphics. I've tried the following:

[LIST]
[*]nvidia-xconfig
[*]change resolution in config files
[*]restore xorg.conf from backup
[/LIST]
I still get the tty console when I boot into Ubuntu. TIA

---

### Post by The Woozy Fieldmouse on 2011-04-26
I posted a walkthrough of how I got my 460 working with the Nvidia drivers [here]("http://kubuntuforums.net/forums/index.php?topic=3116278.msg259563#msg259563"). It might help.

---

### Post by rklapp on 2011-04-27
Thanks for the suggestion. I'm having trouble with stopping the x server in Ubuntu 10.10 so I can install the file I d/l from the nvidia website. With the downloaded and the proprietary driver, I boot into the prompt and have to use failsafe graphics. When I deactivate the driver, then I boot into the low-res screen but hangs while loading the Recovery Mode. 

I have no kdm installed and can't find it. I have lxdm but doesn't work. When I try gdm, it gives me a blank cursor screen and the keyboard does nothing.

I get the following:
```
$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation Device 1200 (rev a1)
02:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)

$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600         0.0  
   640x480         0.0
```I need to install the new driver from the website so it can recognize the 560 gpu. Any suggestions? TIA

---

### Post by Perfect Storm on 2011-04-27
If the Nvidia driver from addition Driver doesn't support your card, go get the latest Nvidia driver from PPA instead. It's easier and less messy.

[http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html)

---

### Post by realzippy on 2011-04-27
[I]$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation Device 1200 (rev a1)
02:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)[/I]

...looks like you have 2 nvidia graphic cards. ??????????

---

### Post by rklapp on 2011-04-27
Yes, I have a 560ti and 9800gt. I had a 470SC but sold it the other day to an interested buyer. The 2nd card runs as physx and I use it for distributed computing (folding.stanford.edu).

The problem with the PPA install is that (1) the beta driver doesn't support the 560ti (but the new certified driver does) and (2) I don't have Hardware Drivers on my install so I can't check the version. 

Any other suggestions? TIA

---

### Post by realzippy on 2011-04-27
It can only take a few hours until xswat updates the driver from 270.xx.04 to the certified 270.xx.06....
If you cannot wait,you had to install the driver manually.

---

### Post by rklapp on 2011-04-27
I got it to work using the package I found here. Thanks all for your help.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+packages](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+packages)

---

