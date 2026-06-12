---
title: "Hello again"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by GSI on 2010-01-06
Hello again! Just 10 minutes ago I visited the forums again (haven't been here for 2 months) and I decided to install Ubuntu again on my PC. So my question is Will be 5GB of space be enough for ubuntu 9.10 to work normaly?

Thanks in advance! :)

---

### Post by Sef on 2010-01-06
8 - 10 gb is what is recommended.  You can do with less, but may run into problems.

[Requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements"):

> **Bare Minimum requirements**

 It should be possible to get Ubuntu running on a system with the following minimum hardware specification, although it is unlikely that the system would run well. You should use the *Alternate install CD* to attempt such an installation. 

[LIST]
[*]300 MHz x86 processor 
[*]64 MB of system memory (RAM) 
[*]At least 4 GB of disk space (for full installation and swap space) 
[*]VGA graphics card capable of 640x480 resolution 
[*]CD-ROM drive or network card 
[/LIST]
 
**Recommended minimum requirements**

 Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly. 

[LIST]
[*]700 MHz x86 processor 
[*]384 MB of system memory (RAM) 
[*]8 GB of disk space 
[*]Graphics card capable of 1024x768 resolution 
[*]*Sound card* 
[*]*A network or Internet connection* 
[/LIST]
**Note:** All 64-bit (x86-64) PCs should be able to run Ubuntu. Use the 64-bit installation CD for a 64-bit-optimised installation. 

---

### Post by mocoloco on 2010-01-06
Yes it will work fine, though you won't have much space left for personal files of significant size, like music, movies, etc.

---

### Post by lewisforlife on 2010-01-06
Have a look at [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

It looks like you should be fine, but if you want to install many apps/store a lot of data, you might be in trouble.

You might look into Xubuntu, it has much lower system requirements.

---

### Post by GSI on 2010-01-06
> **mocoloco said:**
> Yes it will work fine, though you won't have much space left for personal files of significant size, like music, movies, etc.

The 5GB partition will be JUST for the OS I have other partitions for my personal data :) 

And another question
Will there be any problem with my Nvidia GeForce2 video card?

---

### Post by adelphos on 2010-01-06
> **GSI said:**
> The 5GB partition will be JUST for the OS I have other partitions for my personal data :) ?

Yeah, that should be fine... unless you want to install both GNOME and KDE, several IDE's, or lots of games.

---

### Post by GSI on 2010-01-06
Well I do plan to play games... What should I do?

---

### Post by adelphos on 2010-01-06
> **GSI said:**
> Well I do plan to play games... What should I do?

Well, I just meant that the base Ubuntu installation will take about 2-3 GB, if I recall correctly. So, if these are large games that take between 500 MB and 1 GB, you won't have the room. Of course, not all games are that large. I'm assuming that this partition is for root, and that your only other Linux partition is mounted as /home. So, if you want play games like Quake, Unreal Tournament, Doom 3, etc. in Linux, you'll need more space.

---

### Post by GSI on 2010-01-06
But I'm not saving games on the Linux Partition.. I have another partition for games,music etc.

---

### Post by GSI on 2010-01-06
Guys I need some help...

If I enable the Nvidia Drivers from System-->Administration-->Hardware Drivers I get Max resolution 640x480 and refresh rate 60hz

Help me please! I dont know what to do!

---

### Post by Bartender on 2010-01-06
Fire up a terminal and either copy/paste the below or type it in 

```
lspci
```

Post the whole thing or just the line that says something about "video controller".  Anyone who wants to help will at least want to know the graphics chipset.

---

### Post by GSI on 2010-01-07
After the resolution got bugged I removed the driver and updated the OS and after that everything is fine! I have high resolution,effects and games now.Thank you guys!

---

