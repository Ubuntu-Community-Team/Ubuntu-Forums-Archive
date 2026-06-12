---
title: "Overheating issue"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by Matamane on 2009-08-23
This is Day 2 of my first Ubuntu experience, and overall I am happy, except for one thing. I've tried a few things already, like editing my etc/modules, but nothing has worked. Whenever I play a video file, my computer shuts down from overheat, at least that is what I think it is. I have a Toshiba Satellite L300D with standard configurations. I am going to cross post since I don't know if this is the right place, but any help would be great.

---

### Post by Bartender on 2009-08-23
Which version of Ubuntu you running?  A year or two back I used to see lots of threads about laptops overheating, but it seems that later versions of Ubuntu do a better job of power mgmt.

---

### Post by Matamane on 2009-08-23
Jaunty Jackalope

---

### Post by tedtester on 2009-08-23
Download and install your desired flavor of Ubuntu (Ubuntu/Kubuntu/Xubuntu) in the 32 bit or 64 bit version (the 64 bit version takes a bit of work to get set up, so only use the 64 bit version if you are prepared for a little work,) EDIT: After beating my head against it for quite a while I would suggest against installing the 64 bit version. I ended up going back to the 32 bit version. If you have installed Ubuntu before you know the drill, if not, follow the prompts the installation gives you. And though it is less pretty, I recommend the alternate (non-graphical) install, because I have had less luck with the live cd install.

Step 2: Install omnibook module.

Older Toshiba laptops use their own proprietary bios that required the toshiba_acpi module to be compiled with the kernel. Toshiba now uses the Phoenix bios, which means that this has to be done another way, which is a bit deceptive. You have to download the omnibook module (Omnibook is actually an HP model laptop) which will allow these functions. You can download the module source package here: [http://packages.kirya.net/debian/pool/main/o/omnibook/omnibook-source_2.20070211+svn20071217-1_all.deb](http://packages.kirya.net/debian/pool/main/o/omnibook/omnibook-source_2.20070211+svn20071217-1_all.deb) Edit: The omnibook-source package has been updated, which broke the link. Updated versions of the omnibook-source can be found at [http://packages.kirya.net/debian/pool/main/o/omnibook/](http://packages.kirya.net/debian/pool/main/o/omnibook/)
Install the source, extract it, install dependencies, and install the module in the terminal:

```

sudo dpkg -i omnibook-source_2.20070211+svn20071217-1_all.deb
cd /usr/src
tar -xvf omnibook-source_2.20070211+svn20071217-1_all.tar.bz2
cd modules/omnibook
sudo apt-get install build-essential linux-headers-`uname -r`
sudo make install

```

The install may say it lacks a few other dependencies which can be installed with apt-get. Once the source is installed, the module should be able to be loaded, however it needs a special argument when it is loaded or else it won't work.

```

sudo depmod -a
sudo modprobe omnibook ectype=11

```


If everything was set up correctly, you will most likely hear your fan kick on and the screen brightness change. You can now change the brightness with the function keys, and the fan will start up when you turn on the laptop. Make sure the module loads when you boot by adding "omnibook ectype=11" to the bottom of your /etc/modules file.

---

### Post by Matamane on 2009-08-23
It says Omnibook not found

---

### Post by studiodude on 2009-08-23
I am afraid I cant comment on the software solution above, and I am sure it is necessary and should be followed, but I had a very similar problem on a Dell Vostro - any video just put the Laptop to sleep.  I have to say that Vista did it much more frequently, but it still occured under a fresh install of 9.04. 

 The solution I found on another forum and that was to get hold of the service manual and dismantle the computer to re apply a decent squirt of thermal paste between the cpu and heat dissipater.  I admit I was skeptical that going throughall that was not gonna work but since I did this the computer has not shut down once in almost a couple of months.  Under Vista the shut down was a daily occurrence - under Ubuntu only video caused it so that was some improvement but since applying the paste NO shut downs at all.  It was a bit fiddly to do, but if you take your time with the service manual the procedure was no more difficult than a decent Mecano kit. On my experience I can highly recommend going through it even as a precautionary measure once you go through the software solution posted above. 

 The forum I found the solution  on (cant find a link to it right now, sorry) suggested that its a more frequent problem than a failing fan and that some manufacturers use poor quality or not enough paste in the first place.

 Hope you get it sorted.

---

### Post by tedtester on 2009-08-23
> **Matamane said:**
> It says Omnibook not found

[http://packages.kirya.net/debian/pool/main/o/omnibook/omnibook-source_2.20070211+svn20090714b-1_all.deb](http://packages.kirya.net/debian/pool/main/o/omnibook/omnibook-source_2.20070211+svn20090714b-1_all.deb)

---

