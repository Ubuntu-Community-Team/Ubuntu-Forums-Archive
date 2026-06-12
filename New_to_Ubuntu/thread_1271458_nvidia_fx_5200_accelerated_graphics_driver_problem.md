---
title: "nvidia fx 5200 accelerated graphics driver problems"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by joebanjo on 2009-09-20
I have an nvidia fx 5200 graphics card and for some reason the accelerated graohics driver just wont activate.  I've looked through the forums and although there are people with the same problem as me who have been able to fix, the solutions just don't work
```
sudo dpkg-reconfigure xserver-xorg
```
this for some reason just gives me keyboard options
Please Help.
thankyou

---

### Post by j.bell730 on 2009-09-20
Have you tried [Envy]("http://albertomilone.com/nvidia_scripts1.html")?

```
sudo apt-get install envy
```

---

### Post by joebanjo on 2009-09-21
I did that and opened Envy and started it installing the driver and it popped up this message:   p, li { white-space: pre-wrap; }  EnvyNG has detected that the headers for your kernel are missing and cannot be installed
what are kernel headers?  and how do I get them?
thanks

---

### Post by j.bell730 on 2009-09-22
Try this:
```
sudo apt-get install linux-kernel-headers
```

---

### Post by mike555 on 2009-09-22
You might be better off running envy from terminal , I think you just type sudo envy and it will give you a text menu ........

---

### Post by gwpritch on 2009-09-22
I had the same problem with my fx5500.  Delete all nvidia drivers from your system, reboot, then reinstall from the repos using the restricted drivers app. Reboot...all should be well

---

### Post by joebanjo on 2009-09-22
> **j.bell730 said:**
> Try this:
```
sudo apt-get install linux-kernel-headers
```
It said I have to select one.  Any ideas on which one i need?

---

### Post by joebanjo on 2009-09-22
> **gwpritch said:**
> I had the same problem with my fx5500.  Delete all nvidia drivers from your system, reboot, then reinstall from the repos using the restricted drivers app. Reboot...all should be well
How do I delete the drivers?

---

### Post by joebanjo on 2009-09-22
> **mike555 said:**
> You might be better off running envy from terminal , I think you just type sudo envy and it will give you a text menu ........
didn't open in terminal

---

### Post by credobyte on 2009-09-22
```
sudo apt-get install nvidia-glx-173

```

NVidia FX5200 .. works for me.

---

### Post by RedRat on 2009-09-22
I believe you want to install envyNG:
```
sudo apt-get envyng install
```

You might also want to install nvidia-settings:
```
sudo apt-get nvidia-settings
```


Once installed, open a terminal and run:
```
gksudo envyng
```

This will open EnvyNG window version. There should be options for your particular card.

Once installed, then run nvidia-settings from the terminal using gksudo:
```
gksudo nvidia-settings
```

With nvidia-settings you can also set your monitor and resolution.

---

### Post by joebanjo on 2009-09-25
> **credobyte said:**
> ```
sudo apt-get install nvidia-glx-173

```NVidia FX5200 .. works for me.
Its already instaled

---

### Post by joebanjo on 2009-09-25
> **RedRat said:**
> I believe you want to install envyNG:
```
sudo apt-get envyng install
```You might also want to install nvidia-settings:
```
sudo apt-get nvidia-settings
```
Once installed, open a terminal and run:
```
gksudo envyng
```This will open EnvyNG window version. There should be options for your particular card.

Once installed, then run nvidia-settings from the terminal using gksudo:
```
gksudo nvidia-settings
```With nvidia-settings you can also set your monitor and resolution.
I have envyNG, it won't run from code and nvidia settings puts up this error message "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. " when i try nvidia-xconfig, nothing happens.

---

### Post by RedRat on 2009-09-25
> **joebanjo said:**
> I have envyNG, it won't run from code and nvidia settings puts up this error message "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. " when i try nvidia-xconfig, nothing happens.

What do you mean that envyng won't run??? Please explain. Do you have it installed? Go to Synaptic and make sure that it is installed. You should be able to run envyng from the terminal using either gksudo or sudo, i.e., gksudo envyng or sudo envyng.

That it does not run seems to indicate that you do not have it installed. Nvidia-settings will not run and it will give you that error message if you do not have the nvidia driver installed.

---

### Post by joebanjo on 2009-09-25
> **RedRat said:**
> What do you mean that envyng won't run??? Please explain. Do you have it installed? Go to Synaptic and make sure that it is installed. You should be able to run envyng from the terminal using either gksudo or sudo, i.e., gksudo envyng or sudo envyng.

That it does not run seems to indicate that you do not have it installed. Nvidia-settings will not run and it will give you that error message if you do not have the nvidia driver installed.
well when i run it via terminal it says i need to provide a parameter, and when i do that nothing happens.  it says i have the nvidia driver installed when i try to install it through

---

### Post by RedRat on 2009-09-25
> **joebanjo said:**
> well when i run it via terminal it says i need to provide a parameter, and when i do that nothing happens.  it says i have the nvidia driver installed when i try to install it through
If you need to see what the parameters are, type in:
```
envyng --help
```This will give you a list of what to enter. Now I am running 8.04 and so mine might be slightly different from yours since you are running 9.04. 

I suggest that you run 
```
envyng -g
```this is for the gnome gui.

It will ask you for your password and throw up a GUI window and you will be able to select which driver (either ATI or NVidia, then you can have auto-detection, manual selection, or even the unistallation of the driver. Since you have an Nvidia card, select NVIDIA from the box on the left. 

You might want to try auto-detection, that may or may not work for your particular card--I don't how old it might be. If that fails, then you might have to do a manual install. You will have to reboot and if the Nvidia driver is successfully installed you ought to see the Nvidia splash screen come up upon reboot and before log in splash.

Unless the driver is installed, you won't get anywhere with nvidia-settings since this is the handmaiden to the driver.

---

### Post by joebanjo on 2009-09-25
> **RedRat said:**
> If you need to see what the parameters are, type in:
```
envyng --help
```This will give you a list of what to enter. Now I am running 8.04 and so mine might be slightly different from yours since you are running 9.04. 

I suggest that you run 
```
envyng -g
```this is for the gnome gui.

It will ask you for your password and throw up a GUI window and you will be able to select which driver (either ATI or NVidia, then you can have auto-detection, manual selection, or even the unistallation of the driver. Since you have an Nvidia card, select NVIDIA from the box on the left. 

You might want to try auto-detection, that may or may not work for your particular card--I don't how old it might be. If that fails, then you might have to do a manual install. You will have to reboot and if the Nvidia driver is successfully installed you ought to see the Nvidia splash screen come up upon reboot and before log in splash.

Unless the driver is installed, you won't get anywhere with nvidia-settings since this is the handmaiden to the driver.
I've ried this already and my kernel headers are missing (see page 1)
thanks for the help though

---

### Post by RedRat on 2009-09-25
> **joebanjo said:**
> I've ried this already and my kernel headers are missing (see page 1)
thanks for the help though

Have you tried the suggestion by [j.bell730]("http://ubuntuforums.org/member.php?u=563127") on page 1, that is:
```
sudo apt-get install linux-kernel-headers
```Did this work for you? For me, I have installed a package called linux-libc-dev and Envy works for me. Now you are running 9.04 so it might be different for you.

---

### Post by joebanjo on 2009-09-25
> **RedRat said:**
> Have you tried the suggestion by [j.bell730]("http://ubuntuforums.org/member.php?u=563127") on page 1, that is:
```
sudo apt-get install linux-kernel-headers
```Did this work for you?
it says i have to specify which kernel headers, but I don't know what they are

---

### Post by RedRat on 2009-09-25
> **joebanjo said:**
> it says i have to specify which kernel headers, but I don't know what they are
Open Synaptic and click on "ALL" in the left hand panel, then go to the search function and enter in:
linux-kernel-headers
And see what that brings you.

---

### Post by sandyd on 2009-09-25
```

sudo envyng -t

```

---

