---
title: "About NVIDIA or GTK problem"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by alfa_80 on 2011-08-15
Hi,

I am facing a problem when running "sudo startx". It returns some messages saying that > 
NVIDIA(0): Failed to initialize the GLX module; please check in your x  server and, that the glx module has been loaded in your x server and  that the module is the NVIDIA GLX module. If you continue to encounter  problems, Please try reinstalling the NVIDIA driver.


I have nvidia-current and nvidia-common installed. I'm also not sure which installed NVIDIA packages will cause conflict. Because of this  I still cannot solve my visualization problem..It's mentioned that I'm using nvidia corporation rev 162 for the chipset when retrieve for /var/log/Xorg.0.log

I'm really clueless how to fix this..Any idea?

Thanks in advance..

---

### Post by realzippy on 2011-08-15
What do you want to achieve?
Why sudo?
...*"visualization problem"*?

---

### Post by alfa_80 on 2011-08-15
> **realzippy said:**
> What do you want to achieve?
Why sudo?
...*"visualization problem"*?

I actually want to get back my normal ubuntu screen. For the time being I just can work on console.

I've tried to run "startx" without sudo but it complains that "X:user not authorized to run the X server, aborting..etc" kind of permission problem.

*"visualization problem" = normal ubuntu desktop* environment, not black screen..

---

### Post by realzippy on 2011-08-15
> **alfa_80 said:**
>  want to get **back** my normal ubuntu screen.  

So once it worked.
So what have you done?
What happened?

---

### Post by alfa_80 on 2011-08-15
> **realzippy said:**
> So once it worked.
So what have you done?
What happened?

Once it worked, I've tried to tweak my machine via synaptic manager to install libgtk(I forgot the exact name) and libgtkmm..there're some packages were removed at that time I guess, perhaps gtk-related or nvidia-related stuff. Suddenly, when I try to open an application, it stucks and not opening, then, I rebooted my machine, then I got a blank screen..huhu

Any thought is really appreciated..

---

### Post by realzippy on 2011-08-16
First try to start desktop.
Remove xorg.conf:

```
sudo rm /etc/X11/xorg.conf
```
then
```
startx
```

If it not works,try to boot in recovery mode.
Press "shift" when booting,choose 1rst recovery kernel,failsafe graphics.
Then purge/reinstall nvidia-current.

---

### Post by VinDSL on 2011-08-16
> **alfa_80 said:**
> I'm really clueless how to fix this..Any idea?

Thanks in advance..
I test Ubu Dev Branches, and  run across this all the time - yesterday being the most recent.

Here's the clue...

```

[...] Please try reinstalling the NVIDIA driver.

```

What I do is boot into recovery mode (root with network), at grub, and "wash, rinse and set" nVidia, e.g. remove and purge nvidia-current, re-install nvidia-current, then reboot.

---

### Post by alfa_80 on 2011-08-16
> **realzippy said:**
> First try to start desktop.
Remove xorg.conf:

```
sudo rm /etc/X11/xorg.conf
```then
```
startx
```
Then purge/reinstall nvidia-current.

For these steps, how to get to non-recovery mode? What to press?

---

### Post by alfa_80 on 2011-08-16
> **VinDSL said:**
> I test Ubu Dev Branches, and  run across this all the time - yesterday being the most recent.

Here's the clue...

```

[...] Please try reinstalling the NVIDIA driver.

```What I do is boot into recovery mode (root with network), at grub, and "wash, rinse and set" nVidia, e.g. remove and purge nvidia-current, re-install nvidia-current, then reboot.

I've just tried this, it doesn't work, as it can  go maximum at "ubuntu sound" and cursor plus blank screen..

---

### Post by alfa_80 on 2011-08-16
> 
If it not works,try to boot in recovery mode.
Press "shift" when booting,choose 1rst recovery kernel,failsafe graphics.
Then purge/reinstall nvidia-current.


I didn't get this instruction, I can go to recovery mode from the grub menu, but after I press "shift", it directly goes to recovery menu, how do I choose 1st recovery kernel then? it only has failsafeX there, but not failsafe graphics..

Thanks..

---

### Post by VinDSL on 2011-08-16
> **alfa_80 said:**
> I've just tried this, it doesn't work, as it can  go maximum at "ubuntu sound" and cursor plus blank screen..
You have to remove/purge/install nvidia-current from the root command line (CLI) in the grub menu (recovery mode).

Is this what you did, and it failed?

---

### Post by alfa_80 on 2011-08-16
> **VinDSL said:**
> You have to remove/purge/install nvidia-current from the root command line (CLI) in the grub menu (recovery mode).

Is this what you did, and it failed?

Yes exactly, in recovery mode at root I've run "apt-get remove --purge nvidia-current" and "apt-get install nvidia-current", however, I'm still left with the problem..Any ideas?

Thanks anyway..

---

### Post by realzippy on 2011-08-16
Maybe just purge it,not reinstall.
Then reboot.Maybe selecting older kernel helps...

---

### Post by alfa_80 on 2011-08-16
> **realzippy said:**
> Maybe just purge it,not reinstall.
Then reboot.Maybe selecting older kernel helps...

> 
If it not works,try to boot in recovery mode.
Press "shift" when booting,choose 1rst recovery kernel,failsafe graphics.
Then purge/reinstall nvidia-current. 


I am now confused what you meant by purge it, which one? Very sorry for not getting it..

---

### Post by alfa_80 on 2011-08-16
> **alfa_80 said:**
> I am now confused what you meant by purge it, which one? Very sorry for not getting it..

Oh, I've overlooked the word "may be"..I got what you meant..

---

### Post by alfa_80 on 2011-08-16
> **realzippy said:**
> Maybe just purge it,not reinstall.
Then reboot.Maybe selecting older kernel helps...

Still doesn't work including selecting older kernels step taken..huhu

---

### Post by realzippy on 2011-08-16
*.there're some packages were removed at that time I guess,*

Since we do not know what exactly was uninstalled,I suggest a shot in the dark:
```

sudo nvidia-settings --uninstall
sudo apt-get remove --purge nvidia*
sudo apt-get remove --purge xserver-xorg-video-nv xserver-xorg-video-nouveau
sudo apt-get install nvidia-common sudo apt-get install xserver-xorg-video-nouveau
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install --reinstall ubuntu-desktop


```

---

### Post by alfa_80 on 2011-08-16
> **realzippy said:**
> *.there're some packages were removed at that time I guess,*

Since we do not know what exactly was uninstalled,I suggest a shot in the dark:
```

sudo nvidia-settings --uninstall
sudo apt-get remove --purge nvidia*
sudo apt-get remove --purge xserver-xorg-video-nv xserver-xorg-video-nouveau
sudo apt-get install nvidia-common sudo apt-get install xserver-xorg-video-nouveau
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install --reinstall ubuntu-desktop


```

I've tried the following at my first several attempts but it does not work, is that a valid one?
```

sudo nvidia-settings --uninstall

```

---

