---
title: "WoW / Graphics Drivers?"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by I am a Total Noob on 2011-06-30
So, I just re-installed Ubuntu onto my laptop. It was having issues with windows 7, so I went to Ubuntu (which I like more anyways). 

PC Specs:
Intel Core 2 Duo T6600 2.2GHz
Nvidia GeForce 130M
4 GB DDR3 Memory

I have WoW running on PlayOnLinux with no problems except for my graphics being totally laggy. On my windows end it wasn't an issue, not sure why it is now. 
When I go into my drivers I get:
[[IMG]http://img204.imageshack.us/img204/5991/nopropdrivers.th.png[/IMG]](http://img204.imageshack.us/i/nopropdrivers.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

So, I'm starting to think my graphics drivers aren't active...

Anyone know how I can fix this?
Please let me know :] :popcorn:

---

### Post by Perfect Storm on 2011-06-30
Hi,

Lets see if the video card driver is activated, please open the terminal and post the outcome of those commands:
```
lspci |grep VGA

dmesg |grep NVIDIA

glxinfo | grep direct
```

---

### Post by I am a Total Noob on 2011-06-30
[IMG]http://i1239.photobucket.com/albums/ff517/EricTheSTorm/Ubuntu/lspcihaha.png[/IMG]

Thats the img.

---

### Post by wildmanne39 on 2011-06-30
Hi, try this, it will most likely improve you graphics.
    Install CompizConfig Settings Manager from either the Software Center, or Synaptic.
    Click on the Composite tab, and un-check Detect refresh rate.
    Back to main menu.
    Click on the OpenGL tab.
    Uncheck Sync to Vblank.

---

### Post by I am a Total Noob on 2011-06-30
> **wildmanne39 said:**
> Hi, try this, it will most likely improve you graphics.
    Install CompizConfig Settings Manager from either the Software Center, or Synaptic.
    Click on the Composite tab, and un-check Detect refresh rate.
    Back to main menu.
    Click on the OpenGL tab.
    Uncheck Sync to Vblank.

It says its installed but I can't access it.
The Settings Manager itself can't be downloaded on my end for one reason or another.

---

### Post by wildmanne39 on 2011-07-01
Hi, what errors are you getting when you try to install it?

---

### Post by I am a Total Noob on 2011-07-01
> **wildmanne39 said:**
> Hi, what errors are you getting when you try to install it?
Package Dependencies Cannot Be Resolved.

---

### Post by Perfect Storm on 2011-07-01
Try first:
```
sudo apt-get update && sudo apt-get upgrade
```
copy and paste the outcome, you can use **[ code] [/ code]** (without the space)tags around the outcome so it's more readable on the forums.

---

### Post by JumpinJimminy on 2011-07-01
I recently upgraded to 10.04 Lucid. I have noticed lagging graphics/video/etc as well. I know my graphics card isn't the greatest but I can still try and squeeze as much performance as possible out of it. 

The outcome to the commands you listed were:

```
jimmy@base:~$ lspci |grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
jimmy@base:~$ dmesg |grep NVIDIA
jimmy@base:~$ glxinfo | grep direct
direct rendering: Yes
```

Nothing followed the second one???

I then installed CompizConfig Settings Manager via Ubuntu Software Center. . There are 2 options: "**Advanced Desktop Effects Settings (ccsm)**, my choice, or **Simple CompizConfig Settings Manager**.

In 10.04 Lucid LTS the *Detect Refresh Rate* and *Sync to VBlank* options are under General>General Options>Display Tab.

What would be a recommended refresh rate setting?

---

### Post by I am a Total Noob on 2011-07-01
> **Artificial Intelligence said:**
> Try first:
```
sudo apt-get update && sudo apt-get upgrade
```copy and paste the outcome, you can use **[ code] [/ code]** (without the space)tags around the outcome so it's more readable on the forums.

A ton of stuff updated and upgraded - too much to post that's for sure.
But, I need to get some sleep.
I'll give running the game a shot once again tomorrow. :]

Thanks for all the help, feel free to continue posting ideas :]

---

### Post by wildmanne39 on 2011-07-01
> **JumpinJimminy said:**
> I recently upgraded to 10.04 Lucid. I have noticed lagging graphics/video/etc as well. I know my graphics card isn't the greatest but I can still try and squeeze as much performance as possible out of it. 

The outcome to the commands you listed were:

```
jimmy@base:~$ lspci |grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
jimmy@base:~$ dmesg |grep NVIDIA
jimmy@base:~$ glxinfo | grep direct
direct rendering: Yes
```

Nothing followed the second one???

I then installed CompizConfig Settings Manager via Ubuntu Software Center. . There are 2 options: "**Advanced Desktop Effects Settings (ccsm)**, my choice, or **Simple CompizConfig Settings Manager**.

In 10.04 Lucid LTS the *Detect Refresh Rate* and *Sync to VBlank* options are under General>General Options>Display Tab.

What would be a recommended refresh rate setting?
Hi, refresh rate should be 60.

---

