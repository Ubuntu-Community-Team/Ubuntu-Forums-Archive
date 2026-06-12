---
title: "Failed to load NVIDIA kernel module"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by barbedsaber on 2010-11-27
At boot, I get an error, stating that ubuntu is going to start in low graphics mode because:

```
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module
(EE) NVIDIA(0): ***Aborting***
(EE) Screen(s) found, but none have a usable configuration
```

I just click restart X and ubuntu works (I assume I'm using the onboard graphics chip on the motherboard, but I would like to use my dedicated graphics card)

lspci | grep VGA gives

```
02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)

```

modprove nvidia gives

```
)FATAL: Module nvidia not found
```

synaptic says I have 
[LIST]
[*]nvidia-96
[*]nvidia-96-glx
[*]nvidia-settings
[*]xserver-xorg-video-noeveau
[*]xserver-xorg-video-nv
[/LIST]
All installed and up to date

my xorg.conf is here [http://pastebin.com/QTYJEAxn](http://pastebin.com/QTYJEAxn)

(I think that's all the troubleshooting info)

how do I fix this? I assume I have the packages installed, but they are not being called upon by the kernel to display stuff? or I am missing a module, or a module is mislabled. IDK :confused::confused:

what do I need to do to use my geforce card?

cheers for any help.

---

### Post by Locke_99GS on 2010-11-27
Try running *sudo dpkg-reconfigure xserver-xorg*, then afterwards *sudo insmod nvidia* and *sudo nvidia-xconfig* and see if that fixes the issue.

---

### Post by barbedsaber on 2010-11-27
> **Locke_99GS said:**
> Try running *sudo dpkg-reconfigure xserver-xorg*, then afterwards *sudo insmod nvidia* and *sudo nvidia-xconfig* and see if that fixes the issue.

```
mynameistux@Koala:~$ sudo insmod nvidia
insmod: can't read 'nvidia': No such file or directory

```

which direction should I point insmod to?

---

### Post by barbedsaber on 2010-11-27
it's-been-two-hours-and-I-have-HD-movies-to-watch-bump

---

### Post by cchhrriiss121212 on 2010-11-27
Did you recently update to a new kernel? If so try an older one out.

---

### Post by barbedsaber on 2010-11-27
> **cchhrriiss121212 said:**
> Did you recently update to a new kernel? If so try an older one out.

just tried an older kernel from grub, no difference.

for what it's worth, I've never had this card working on this computer, it's a relatively new install

---

### Post by Jose Catre-Vandis on 2010-11-27
If you did recently update to a newer kernel number, all you need to do is click on to start ubuntu in a low graphics mode, open up hardware drivers, deactivate nvidia driver, then reactivate it, reboot, job done.

---

### Post by barbedsaber on 2010-11-27
> **Jose Catre-Vandis said:**
> If you did recently update to a newer kernel number, all you need to do is click on to start ubuntu in a low graphics mode, open up hardware drivers, deactivate nvidia driver, then reactivate it, reboot, job done.

the hardware drivers thing says there are no drivers in use, and none are available. I know that the nvidia-96 driver works with this card, should I be trying to fix the hardware driver program instead of fixing the kernel module manually?

---

### Post by barbedsaber on 2010-11-27
I FIXED IT
I installed a package called ```
nvidia-96-modalias
```
that fixed the hardware driver finding program, I did what Jose Catre-Vandis said, and hey presto, it works like a charm
> **Jose Catre-Vandis said:**
> If you did recently update to a newer kernel number, all you need to do is click on to start ubuntu in a low graphics mode, open up hardware drivers, deactivate nvidia driver, then reactivate it, reboot, job done.

Jose, I reckon I owe you a beer.
cheers for the solution mate :D

---

### Post by Jose Catre-Vandis on 2010-11-28
@barbedsaber
You have one for me, too cold for beer here, and you may need to drown your sorrows after the Ashes ;)

---

