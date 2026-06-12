---
title: "[SOLVED] how to check nvidia card type from CLI?"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by minsf on 2008-12-04
hi 
this is probably a quick one, please forgive me being a newbie...
how do i check the version of my nvidia card from the CLI?
i think i have geforce4 440 go 32MB, but i want to be sure before i download the driver from nvidia.

---

### Post by scragar on 2008-12-04
I think you should use envy if you are running ubuntu, since envy has a command line option that detects and installs the driver on it's own, with no risk of you getting something wrong.
```
lspci | less
```
Will let you look around for your graphics card, I know there must be a better way of finding it though.

---

### Post by mikewhatever on 2008-12-04
sudo lshw -C display

---

### Post by CatKiller on 2008-12-04
> **minsf said:**
> i think i have geforce4 440 go 32MB, but i want to be sure before i download the driver from nvidia.

Don't download the driver from NVidia's website. If you do, you'll then be asking how to stop X, and how to run as root. Use the package manager instead.

Either go to System -> Administration -> Hardware Drivers, or find the appropriate nvidia-glx package in Synaptic, or run Envy.

---

### Post by minsf on 2008-12-06
"don't download the driver from NVidia's website."-
yeah, good point for other newbies reading this thread later.
actually, a week ago i tried the system>admin>drivers method and after reboot the GUI doesnt load (i got a black screen).
so, unfortunately, i know what you mean by 
"you'll then be asking how to stop X, and how to run as root."
my current plan is to try "method 3" as described on Envy's (tseliot's) website
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.html")
including the extra step for geforce4 440- i believe he calls it point 7.
not sure about the note at the bottom of 
[http://https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeC840]("http://https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeC840")
anyways, i got everything backed up, the liveCD right next to me and a good cup of coffee...
wish me luck :)

---

