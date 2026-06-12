---
title: "Installing nVidia nForce drivers."
date: 2010-03-08
forum: New to Ubuntu
---

### Post by ho0ola on 2010-03-08
Hey yall,
      Im very new to this, but i got my ubuntu working. I was trying to burn the ISO directly from my USB drive.. I had to copy it onto my desktop first to get it to burn to the CD right. ANyway, my resolution and graphics in general are horrible at ubuntu desktop. I would like to use my onboard GeForce4 MX display but cannot find any drivers on nVidias website that are linux specific... How on earth could I possibly get my Mobos onboard display drivers working in Ubuntu?? Any help would be great..
P.S I LOVE ubuntu so far, so simple and user friendly.. and FREE!!!! 
THanks guys;)

---

### Post by MichealH on 2010-03-08
You could edit your xorg.conf see this thread:

[http://ubuntuforums.org/showthread.php?t=815246](http://ubuntuforums.org/showthread.php?t=815246)

---

### Post by gordintoronto on 2010-03-08
Run Administration/Hardware Drivers.

If nothing shows up for your video card, it is just too old.  (I have an old system with an MX400 which worked great until the power supply blew. I used that as an excuse to build a "high-performance" system.)

---

### Post by agnes on 2010-03-08
They seem to have your driver (for Linux) at [http://www.nvidia.com/Download/index5.aspx?lang=en-us]("http://www.nvidia.com/Download/index5.aspx?lang=en-us") so you can just download it from there.

However you could also give [Envy]("http://albertomilone.com/nvidia_scripts1.html") a try, it will select your driver for you, and do the configuring for you, it's easier.

---

### Post by ho0ola on 2010-03-08
thanks guys, i dont have internet on my ubuntu PC, but this one is where i get drivers.. thanks!!

---

### Post by mister_playboy on 2010-03-08
> **gordintoronto said:**
> Run Administration/Hardware Drivers.

If nothing shows up for your video card, it is just too old.  (I have an old system with an MX400 which worked great until the power supply blew. I used that as an excuse to build a "high-performance" system.)

On the two 9.10 installs I have done on computers with NVIDIA cards, no options appeared in Hardware Drivers immediately after install, but the available drivers to download did appear after logging out and back in.

It's worth a shot to try if you don't see any options.

---

### Post by ho0ola on 2010-03-09
OKay thanks guys, i have tried dowloading them off the site.. and linux cant seem to open the file... I tried dling the correct driver twice to make sure it wasnt a download problem. I am not connected to the internet yet on my PC (which is the one runnning ubuntu). SO ive been downloading drivers from a PC in another room, saving them to a flash drive, then copying onto the desktop of my PC and installing. my geForce4 MX doesnt want to work... Oh well, ill wait till i get internet tomorrow!!

Anyway i have a new question :)

When setting up a linksys wireless G card on a linux system, do i need to dl specific drivers from the web? Or i can i use the install CD that came with my hardware? 

You guys rock. UBUNTU!!

---

### Post by gordintoronto on 2010-03-09
Many wireless cards "just work." In other words, the drivers are built in to Ubuntu. Others can be very annoying, but they almost all work eventually.

There are many *different* Linksys Wireless G cards.  To see the specific model, open accessories/terminal and enter the command:
lspci

---

