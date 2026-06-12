---
title: "Compiz is driving me crazy"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by iamjfarrell on 2009-09-24
Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 7150M (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: No path to Compiz found. 

Would you like to know more? (Y/n) y

 In case you did not compile Compiz manually, this will result in Compiz
 failing to run.

I have gotten compiz to work off and on. Mostly off. I can not figure out why it will not work. It used to work until I upgraded. CCSM doesn't work when I try to run it, nor does compiz fusion icon. If anyone could help I would appreciate it.

---

### Post by ~sHyLoCk~ on 2009-09-24
Err, first things first. did you upgrade your kernel? Did you re-install nvidia driver ? Install compiz with all the plugins from synaptic. Then launch ccsm.

---

### Post by iamjfarrell on 2009-09-24
Yeah. I upgraded it all. All my stuff is up to date. I uninstalled compiz and re-installed it via synaptic and it just acted the same.

---

### Post by iamjfarrell on 2009-09-27
I am still searching for an answer. Should I compile compiz manually?

---

### Post by Bölvaður on 2009-09-27
> **iamjfarrell said:**
> I am still searching for an answer. Should I compile compiz manually?

no.

make sure you are still using the correct driver after the update. sometimes with nvidia drivers they are tied down with the old kernel, which means you also have to update the driver.

Does it work if you go to an earlier kernel?

Does it say nvidia : ```
glxinfo | grep client
```


I have much worse geforce card in one of my computers, and it is running like a charm.

---

### Post by powel212 on 2009-09-27
I have experienced similar problems when the mirror I was using for updates was outdated. Try switching to the Main US Mirror and then run updates and see if that helps.

Hope that helps

Powel

---

### Post by iamjfarrell on 2009-09-28
```
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:

```

That is what I got. I haven't checked an older kernal but ever since the upgrade from intrepid to jaunty I have had this problem.

---

### Post by iamjfarrell on 2009-09-28
```
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "/usr/lib/python2.6/dist-packages/FusionIcon/interface.py", line 21, in <module>
    from util import env
  File "/usr/lib/python2.6/dist-packages/FusionIcon/util.py", line 21, in <module>
    import os, compizconfig, ConfigParser, time
ImportError: /usr/lib/python2.6/dist-packages/compizconfig.so: undefined symbol: ccsGetPluginStrExtensions

```

This is what I get when I try to run compiz in terminal

---

### Post by iamjfarrell on 2009-09-28
```
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 38, in <module>
    import compizconfig
ImportError: /usr/lib/python2.6/dist-packages/compizconfig.so: undefined symbol: ccsGetPluginStrExtensions

```

This is what I get when I run ccsm in terminal

---

### Post by iamjfarrell on 2009-09-29
[IMG]http://i231.photobucket.com/albums/ee82/pcknscrnnamessux/bump_sign.jpg[/IMG]

---

### Post by iamjfarrell on 2009-10-02
I have completely uninstalled compiz and all its components via apt-get. I then reinstalled compiz and all its components. Nothing changed of course. What the heck.

---

### Post by misfitpierce on 2009-10-02
Can always get the newest display driver straight from Nvidia

[http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/185.18.36/NVIDIA-Linux-x86-185.18.36-pkg1.run&lang=us&type=GeForce](http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/185.18.36/NVIDIA-Linux-x86-185.18.36-pkg1.run&lang=us&type=GeForce)

run with sudo sh PACKAGENAME.bin or .run or .sh

Can find instructions via google if trouble installing or through here.

---

### Post by iamjfarrell on 2009-10-04
I downloaded and installed the latest driver. It still does not run compiz properly. What am I missing here?

---

