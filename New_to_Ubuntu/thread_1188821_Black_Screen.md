---
title: "Black Screen"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by kurniza on 2009-06-16
Hi,
I am as new as I can get to ubuntu. I installed on a separate, formatted HDD ubuntu 8.10. During the installation I accepted all the default values given. At the end it said that the installation is complete and wanted to restart. I did that, took out the CD and when it restarted a nice orange screen wanted me to log in. I did that, and after I would enter, the screen would stay orange for 15sec and then it all goes black. No buttons are shown whatsoever. Only the mouse pointer stays and it is working. The keyboard isn't(the caps lock light doesn't light when the key is pressed). Any suggestions!? I have a Fujitsu-Siemens Scenic L i845G desktop(it has (1.6 GHz processor and 1 GB RAM and a 82845G/Gl/GE/PE/GV Graphics controller). please help.

---

### Post by renkinjutsu on 2009-06-16
can you log in to a terminal?
when you get to the login screen, instead of logging in there, press ctrl+alt+F1 and you should be brought to a virtual terminal.

Also in this screen, you should be able to see what services are started at boot, check for any failures.
You can login to this terminal.. I'm not very linux savvy myself, but a few things you should always look out for are broken dependencies (that shouldn't be the case, since you have a fresh install) but to fix broken dependencies, use ```
sudo apt-get -f install
``` or if the installation of some packages were interrupted, you can try ```
dpkg-reconfigure -a
```

I might just be wasting your time, but the only thing i can think of is for you to check your filesystem .. to do this, login at the terminal and type ```
sudo init 1
``` and select fsck (your system probably won't be able to unmount the volume though) another way is to type into the terminal ```
sudo touch /forcefsck
``` and do a reboot..

EDIT

I looked through some packages in synaptic and i think you can try to reconfigure this one:
```
sudo dpkg-reconfigure xserver-xorg-input-kbd
```

i don't know much about hardware, but you can also check here if you're having problems
[https://wiki.ubuntu.com/HardwareSupportMachinesDesktops]("https://wiki.ubuntu.com/HardwareSupportMachinesDesktops")
but i'm assuming you've tried Ubuntu on a live CD and everything worked.

for some reason, your description makes me think your /home isn't being mounted, but that's ridiculous! since the default install doesn't mount /home on a different partition.

I just hope my post can help at least a little.. but you should listen to someone who knows what (s)he's talking about

---

### Post by kurniza on 2009-06-16
I forgot to say that even when I turn on ubuntu directly from the CD (without install) it does the same thing a nice orange screen and then a black one with working mouse but not a working keyboard.

---

### Post by renkinjutsu on 2009-06-16
in that case, you should check if your computer is compatible

[https://wiki.ubuntu.com/HardwareSupportMachinesDesktops](https://wiki.ubuntu.com/HardwareSupportMachinesDesktops)

the whole purpose of the liveCD is to see if everything works before making any changes to your harddrive.. Have you checked the disk's integrity? it's important that the ISO file you downloaded isn't corrupt

---

