---
title: "Nvidia driver x not in use?"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by maryalesia on 2010-03-31
Hello! I'm Very New to ubuntu/linux, (as in, as of yesterday I had never before used it), and I have some questions regarding the drivers for my graphics card. I don't know if this is relevant, but I want to run Ubuntu on my Gateway FX laptop, which has a Geforce 9800M GTS graphics card. Please bear with me, because repairing a corrupt driver file in windows is the extent of my computer abilities (damn you, apple mobile device support!). 

Okay, here goes. I was trying to launch the nvidia settings - thingy and it said that the nvidia x driver was not in use, and to do something involving a root command? I know that "root" = sudo, or something, but the comand terminal scares the crap out of me, and I honestly have NO IDEA what I'm doing. So I typed in something along the lines of "sudo apt-get install nvidia-xconfig", typed in my password when prompted, and it came up saying that there was no nvidia x driver package ... err something. 

Did I mention that I got a D in highschool-level computer math?

---

### Post by NCLI on 2010-03-31
Ok, first of all, you want to make sure your system is fully updated ;)

Open the Update Manager from System->Administration->Update Manager, click Check, and install any updates. Then try launching the Hardware Manager from System->Administration->Hardware Drivers. 

There, you should see the driver you need. Install it, then reboot your computer. 

This is the recommended way to install drivers in Ubuntu. If you have installed the nvidia driver in another way, you should uninstall it, then repeat the above.

---

### Post by quadproc on 2010-03-31
> **maryalesia said:**
> 

Okay, here goes. I was trying to... launch the nvidia settings - thingy and it said that the nvidia x driver was not in use, and to do something involving a root command? I know that "root" = sudo, or something, but the comand terminal scares the crap out of me, and I honestly have NO IDEA what I'm doing. So I typed in something along the lines of "sudo apt-get install nvidia-xconfig", typed in my password when prompted, and it came up saying that there was no nvidia x driver package ... err something. 

My comment does not directly address your immediate problem (probably other posters will do that), but I did want to mention that the Hardware Drivers utility does **not** necessarily correctly report the status of drivers.  Once you get your driver installed and working, you may still find that Hardware Drivers reports it as not in use.  I have that very situation on the system that I am using right now, even though it is in use and works fine.

You should be able to find out which driver is in use by looking in your /etc/X11/xorg.conf file if your system has one; look for a line which starts with the word driver and has something in quotes.  That is the driver that X windows is using.

Good luck!

quadproc

---

### Post by chaanakya_chiraag on 2010-03-31
Could you please do the following:
1) Open up a Terminal (Applications -> Accessories-> Terminal).  Don't be afraid! :)
2) Type in ```
cat /etc/X11/xorg.conf
```.  All this does is spit out a huge long thing.  Please copy that stuff into a post here.  (Please put it between CODE tags so that it doesn't overwhelm us!!).
Let's see what exactly X.org (the graphical display) is using.

---

### Post by achase79 on 2010-03-31
go into system->administration->synaptic package manager and search for nvidia-xconfig.  If it is not installed, install it.  Then go to applications->accessories->terminal and type ```
sudo nvidia-xconfig
``` then run ```
sudo nvidia-settings
``` and in that program set your preferences and save the xorg.conf file from that program (there is a button for it).
This should configure your nvidia card correctly.

---

### Post by maryalesia on 2010-03-31
Thank you all so much for your help! 

I have absolutely no idea what I was doing before, but I just un-installed everything I messed around with and followed the first poster's advice. Everything appears to be in working order!!

I still have essentially no idea what I'm doing, so I'll probably be back soon. :D

---

