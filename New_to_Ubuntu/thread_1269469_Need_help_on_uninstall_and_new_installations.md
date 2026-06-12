---
title: "Need help on uninstall and new installations"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by slvfx on 2009-09-18
I bought an inexpensive machine to set up ubuntu linux for use as a webserver. I only bought the tower which is a intel celeron 430 with 1 gb of ram and a 160 gb hard drive. The place I bought it had set up the ubuntu server program for me and he showed it working on his monitor.
 
I went and bought a Sanyo dp19649 tv which included a pc monitor. Brought it home hooked it up, runs the grub but then it goes to a dark screen. Selected the recovery mode which ended up at the same dead screen place.
 
Had a friend who is a test engineer look at it and he said that the screen resolution was set up on a different monitor and we needed to change it. We searched and put multiple code suggestions in it to no avail.
 
He suggested I start over so he emailed be a great looking link to take me through the process of setting up the web server. [http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/) . So I went there and began the process. I burned a dvd with the program on my lap top then put it in the drive assuming an automatic installation startup which would overwrite the existing program. Nothing. So I looked for a fix to uninstall the software. Didn't see anything. Saw a note that said I needed to go into the boot directory and change the boot to the dvd drive. Did that and still nothing.
 
Need help trying to figure out what to do. Thanks in advance.

---

### Post by wrwarwick on 2009-09-18
Are you trying to reload the entire OS on the server? What software are you trying to uninstall?

---

### Post by ikt on 2009-09-18
Are you familiar with the command line?

> So I went there and began the process. I burned a dvd with the program on my lap top

What did you burn and with which program?

If you burned the .iso file directly to the cd it will not work. Need to go through the cd burning software option of 'burn image' and then select the iso image.

Just so you know, by default ubuntu server edition does not have a gui/graphical user interface.

---

### Post by slvfx on 2009-09-18
trying to uninstall ubuntu 9.04 and want to install "Ubuntu 8.04 LTS.
 
If command line is the root shell promp then yes

---

### Post by slvfx on 2009-09-18
My laptop is running vista and i did try to burn it directly to the cd. I will do that part over and try it.

---

### Post by slvfx on 2009-09-18
I didnt know it had no gui. I assume gui would mean like a desktop. I would be using a command prompt.

---

### Post by slvfx on 2009-09-18
Do I need to unzip it before i burn it?

---

### Post by ikt on 2009-09-18
> **slvfx said:**
> I didnt know it had no gui. I assume gui would mean like a desktop. I would be using a command prompt.

Yep, ubuntu server has no desktop, only command prompt, you are able to install a gui later on if you wish.

> **slvfx said:**
> Do I need to unzip it before i burn it?

Nop, there should be an option in your cd burn to burn an image file

[http://img294.imageshack.us/img294/8675/iso.png](http://img294.imageshack.us/img294/8675/iso.png)  is my option.

---

### Post by slvfx on 2009-09-18
nothings happening

---

### Post by slvfx on 2009-09-18
I went back in to the boot directory and rearranged the startup. I rebooted and now i have a message reboot and select proper boot device or insert boot media in selecte3d boot devive abd press key

---

### Post by slvfx on 2009-09-18
Any suggestions

---

### Post by slvfx on 2009-09-18
Any ideas to get me going

---

### Post by ikt on 2009-09-18
if you've burned the cd correctly and have set the bios to boot off the cd first it should work, I'm not sure what else you can do. Best of luck.

---

