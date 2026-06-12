---
title: "taking ubuntu with me to school"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by ben889 on 2011-02-07
how would i take ubuntu with all my setting and programs to school with me i have a 8 gig cruser that i want to use.
 
sorry if this has been answerd before i didnt find it in search
 
 
thanks 
 
 
Ben

---

### Post by Tobey666 on 2011-02-07
[http:/www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download")

These instructions worked very well for me.  Just select USB stick under option 2 and click "show me how."  As far as getting it to work at school, I used my flash drive on my laptop for quite some time, but it can be difficult to use it with a school computer (at least if you want the computer to boot into Ubuntu).  Give it a shot though, it can be a useful tool.

---

### Post by fabricator4 on 2011-02-07
Install Ubuntu onto the USB drive.

In Gparted, Make a 7 GB ext2 partition and a 1 GB swap partition.

Boot from the live CD and start an install

When it asks how you want to install select manual partition

Select the cruzer USB <----IMPORTANT!

Specify the ext2 partition is to be mounted as root.

Specify grub to be installed on the cruzer - eg sdc1 <----- IMPORTANT!

Finish the install

Now, when you boot off the cruzer you will boot into a full version of Ubuntu.

If you want to update the Ubuntu on your cruzer and install programs but don't want to download it all again, copy the .deb files from your hard drive to the cruzer.

The deb files are stored in /var/cache/apt/archives

You can safely delete all the deb files off the cruzer once you're done.  Do NOT delete /var/cache/apt/archives/partial folder or automatic updates and other things will not run. Only delete the .deb files.

Chris

---

### Post by ben889 on 2011-02-07
not sure if i did it right it boots from the usb but it gives me the option to boot from the kernel, recovery  and then the hard drive kernel, recovery but it doesn't have a GUI. I tried the recovery so i could type startx or start failsafe-x but i wont let me. did i do it wrong? should i see the GUI for the grub?


Thanks for getting started in the right direction




Ben

---

### Post by cipherboy_loc on 2011-02-07
Okay first of all:

When you plug in the USB, set the BIOS to boot from USB, you get the menu, right? That is called the GRUB menu, which you really only see if you have multiple OSes on one box (in this case, the USB drive + the internal drive).

To limit it to only the one installed on the USB key, select one of the options (play around until you get the USB key's image, not your desktop), and then open up synaptic. Search for os-prober and remove it. Then open up the terminal and type:

```

sudo update-grub2

```


And that should be it.


Cipherboy

---

### Post by ben889 on 2011-02-07
thanks will do

---

### Post by fabricator4 on 2011-02-08
> **ben889 said:**
> not sure if i did it right it boots from the usb but it gives me the option to boot from the kernel, recovery  and then the hard drive kernel, recovery but it doesn't have a GUI.

Yes, you did great.  You are probably done apart from updating the new system and installing any programs.  Boot the first kernel, and you will get the login screen and then go to your desktop.

Well Done!

---

### Post by mirza_farid on 2011-02-08
sry to ask again, but just for become sure!

is it make a whole OS as a image (or boot file)?
i have a lot of packeages and simulators that i want to make a recovery file of it, 
if i do the thing you said, i will have my whole simulators and softwares?!?!?!:-S
:confused:


is;t real REALY important to me:confused:

---

### Post by cipherboy_loc on 2011-02-08
@mirza: 
Yes, if you either created a LiveUSB key (using unetbootin, etc), or if you installed Ubuntu to the USB key, you will be able to recover your documents. Create a new thread and we should be able to help you (with a bit more information).

@ben:
If you can, please post the grub.cfg (/boot/grub/grub.cfg). If you have a computer at home with two internal drives, and you installed your USB key on that computer, it will have in the grub menu something like HD(3,0). Then if you go to school where they might only have one hard drive, you have to change that line to HD(2,0), etc.


Cipherboy

---

### Post by ben889 on 2011-02-08
sorry it didnt work at home but at my computer at school it works a lil slow but works

---

### Post by fabricator4 on 2011-02-08
> **ben889 said:**
> sorry it didnt work at home but at my computer at school it works a lil slow but works

It should work at home just as it works at school.

Yes it will be slower.  You are booting and running off a USB memory drive, not a HDD.  The flash memory takes more time to do its stuff than a hard drive.

Chris.

---

