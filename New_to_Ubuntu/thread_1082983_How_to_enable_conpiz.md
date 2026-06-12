---
title: "How to enable conpiz"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by jarhead8286 on 2009-02-28
This is a two part question.  I am new to Linux and have just started playing around with Ubuntu on a Dell Dimension 4550 with NVIDIA GeForce4 Ti 4200 AGP8X (128MB) video card.  I would like to enable compiz for eye candy and have no idea how to do it.  Reading this forum, I gather that compiz should be installed already by default.  How do I enable it and will my video card be able to display it?
Second part of the question is:  If my video card is too outdated,  what do you recommend that I replace it with?  I do not play games (if that matters).

In System --> Preferences --> Appearance, Visual Effects are set to Normal

These are my screenshots of the hardware driver and NVIDIA settings:

[Hardware drivers](http://i73.photobucket.com/albums/i232/jarhead8286/Miscellaneous/HardwareDrivers.png)
[NVIDIA Settings](http://i73.photobucket.com/albums/i232/jarhead8286/Miscellaneous/NVIDIASettings.jpg)

---

### Post by howefield on 2009-02-28
Sounds like compiz is already running, you could install compizconfig-settings-manager which will give you a menu option in your system > preferences menu and allow you to set up all the compiz options.

---

### Post by jarhead8286 on 2009-02-28
> **howefield said:**
> Sounds like compiz is already running, you could install compizconfig-settings-manager which will give you a menu option in your system > preferences menu and allow you to set up all the compiz options.
How do I install compizconfig-settings-manager?  From Add/Remove programs?

---

### Post by UbuntuNerd on 2009-02-28
check [HERE](http://my.opera.com/ubuntunerd1/blog/how-to-install-compiz-fusion-in-ubuntu-hardy) and [HERE](http://my.opera.com/ubuntunerd1/blog/how-to-use-compiz-settings-manager)

---

### Post by stoogiebuncho on 2009-02-28
> **jarhead8286 said:**
> How do I install compizconfig-settings-manager?  From Add/Remove programs?

Just click this [link]("apt:compizconfig-settings-manager") ;)

I should add that in the future if you want to install a package and you know the name, you can either go to System > Administration > Synaptic Package Manager and search for the package, or you can simply open a terminal (Applications > Accessories > Terminal) and enter:

```
sudo apt-get install compizconfig-settings-manager
```
(of course, replace compizconfig-settings-manager with the name of the package you want to install.)

---

### Post by jarhead8286 on 2009-02-28
OK... followed the instructions and installed everything, But still can't the cube thing going.  Workspaces are set for 4 Columns by 1 Rows.  What's the secret?

---

### Post by sandyd on 2009-02-28
> **jarhead8286 said:**
> OK... followed the instructions and installed everything, But still can't the cube thing going.  Workspaces are set for 4 Columns by 1 Rows.  What's the secret?
heres what you do..........
type this in terminal
```

compiz --replace

```

THen open up compiz settings manager AGAIN, click on general options
click on Desktop Size
set both horizontal AND vertical to 4

clik back

make sure desktop cube is selected, along with rotate cube, Cube deformation (if you want it to be a cylynder instead of cube), and cube gears

thats all there is to it

---

### Post by howefield on 2009-02-28
> **carlee said:**
> THen open up compiz settings manager AGAIN, click on general options
click on Desktop Size
set both horizontal AND vertical to 4

You only want the horizontal set to four, and vertical and number of desktops set to one.

---

### Post by jarhead8286 on 2009-02-28
I got it!  I didn't know that you have to press [Ctrl]+[Alt]+[Left]/[Right] to switch desktops and [Ctrl]+[Alt]+[Left Mousebutton] to to spin the cube.

---

### Post by howefield on 2009-02-28
Have you tried spinning the cube by pressing the scroll wheel on the mouse, a lot easier than a three fingered salute.

---

### Post by jarhead8286 on 2009-02-28
> **howefield said:**
> Have you tried spinning the cube by pressing the scroll wheel on the mouse, a lot easier than a three fingered salute.
Just tried it, but it didn't work.  Is it clicking the mouse wheel all by itself and scrolling?

---

### Post by howefield on 2009-02-28
Yeah, it is a default setting, click the scroll wheel and drag the mouse to spin the cube. I've never had to do anything to set it this way.

---

### Post by jarhead8286 on 2009-02-28
> **howefield said:**
> Yeah, it is a default setting, click the scroll wheel and drag the mouse to spin the cube. I've never had to do anything to set it this way.
Nope, does not work.  I don't know if it matters, but I have a Logitec wireless mouse.

---

