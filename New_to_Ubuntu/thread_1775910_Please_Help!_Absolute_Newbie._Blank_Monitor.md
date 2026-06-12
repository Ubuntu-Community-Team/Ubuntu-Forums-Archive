---
title: "Please Help! Absolute Newbie. Blank Monitor"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by bluetortilla on 2011-06-05
I have a Panasonic Let's Note laptop with a cracked (indecipherable but working) monitor. I have a 15' LCD Samsung monitor attached via the VGA port. I slicked the drive and installed Ubuntu 11.04. It only works if I boot off the CD or if hold shift and boot it in a safe graphics mode. I suppose it's the graphics card, but XP worked fine. The Displays Panel shows 'Unknown' as in the pic. 
Sometimes holding down shift does nothing.

I want reliable boots and a stable system. Can some PLEASE help config the display? This is my third post.

Thank you.

---

### Post by wildmanne39 on 2011-06-05
> **bluetortilla said:**
> I have a Panasonic Let's Note laptop with a cracked (indecipherable but working) monitor. I have a 15' LCD Samsung monitor attached via the VGA port. I slicked the drive and installed Ubuntu 11.04. It only works if I boot off the CD or if hold shift and boot it in a safe graphics mode. I suppose it's the graphics card, but XP worked fine. The Displays Panel shows 'Unknown' as in the pic. 
Sometimes holding down shift does nothing.

I want reliable boots and a stable system. Can some PLEASE help config the display? This is my third post.

Thank you.
Hi, the problem is no one knows the answer I have a problem like that to and no answer, just so you know you are only allowed to have one post for each problem. What you do after you post wait 24 hours, then bump your thread so it is moved up to the first page again.

---

### Post by jramshu on 2011-06-05
What kind of graphics card do you have?

---

### Post by bluetortilla on 2011-06-06
> **jramshu said:**
> What kind of graphics card do you have?

What can I run to find out? I couldn't find that spec on the web.

---

### Post by alphacrucis2 on 2011-06-06
> **bluetortilla said:**
> What can I run to find out? I couldn't find that spec on the web.

Enter command:

```
sudo lshw -C display
```

Post output back here..

You may also like to see if there are any proprietary drivers to install for you graphics card. Click the Applications button on the left hand dock and then click Additional Drivers.

---

### Post by bluetortilla on 2011-06-06
*-display:0             
       description: VGA compatible controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:9 memory:e8000000-efffffff memory:e0000000-e007ffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: memory:f0000000-f7ffffff memory:e0080000-e00fffff

There were no proprietary drivers available unfortunately.

---

### Post by alphacrucis2 on 2011-06-06
> **bluetortilla said:**
> *-display:0             
       description: VGA compatible controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:9 memory:e8000000-efffffff memory:e0000000-e007ffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: memory:f0000000-f7ffffff memory:e0080000-e00fffff

There were no proprietary drivers available unfortunately.

I don't know too much about intel graphics. Your best bet may be to do a search of the forums or a general google search for Linux Intel 82852/855GM.

---

### Post by bluetortilla on 2011-06-06
> **alphacrucis2 said:**
> I don't know too much about intel graphics. Your best bet may be to do a search of the forums or a general google search for Linux Intel 82852/855GM.

Thanks for your help. At least I got some info on the card.

---

### Post by philinux on 2011-06-06
@bluetortilla

Please dont start multiple threads on same subject. 

I've closed one and deleted the other.

Please try to be patient. It might be that no one has an answer. Hopefully someone does.

---

### Post by Blasphemist on 2011-06-06
bluetortilla-

I've done some research on your intel gpu and will continue to look further. I would like for you to run these things to gather some more information. It is a good thing that you can get safe mode and I think we'll need to try some some kernel mode setting to get better results.

First, run this command.
```
/usr/lib/nux/unity_support_test -p
```
Please post the results. I suspect this will tell us you can't run unity or unity 3d and if so that will tell us which environments to focus on. This command is from this link. [https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

I'd like to know just what happens during an attempt at a normal boot. When does it fail and how? Please see the first post in this thread if you need for troubleshooting the boot if needed. [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Post 1 of that thread is where the solution most likely lies. It shows a lot of information and not all of it is specific to Intel gpu's. It does go through the process of trying some kernel mode settings and does have some intel specific detail. Post 3 shows a way of making temporary kernel mode changes using the live cd and that can also be done from the grub menu.

I don't want to get to far ahead without knowing more of your specifics. That thread is real long and if you want to read more of it, go for it. There are other commands that can be run to get more information but let's try to stay organized and not do things not needed. The good thing is that you are in a better spot than many others using that thread. :D

---

### Post by alphacrucis2 on 2011-06-06
I did find this on ubuntu geek. Seems that there is a launchpad PPA that may help but as the comment says use at own risk:

[http://www.ubuntugeek.com/how-to-install-intel-82852855gm-drivers-in-ubuntu-using-ppa.html]("http://www.ubuntugeek.com/how-to-install-intel-82852855gm-drivers-in-ubuntu-using-ppa.html")

From what I gather the glasen ppa has bleeding edge intel drivers built from git.

Here's the direct link to the launhpad ppa if you want to have a look:

[https://launchpad.net/~glasen/+archive/intel-driver]("https://launchpad.net/~glasen/+archive/intel-driver")

---

### Post by Immolatus on 2011-06-06
you must manually edit xorg.conf to include this monitor if it's not automatically detected.

"screen" section.

intel gma drivers wont fix this or help you manipulate either.

---

### Post by bluetortilla on 2011-06-07
> **philinux said:**
> @bluetortilla

Please dont start multiple threads on same subject. 

I've closed one and deleted the other.

Please try to be patient. It might be that no one has an answer. Hopefully someone does.

Sorry! I tried to delete those threads but I'm so dumb that I couldn't figure out how!
Phil

---

### Post by bluetortilla on 2011-06-08
> **Blasphemist said:**
> bluetortilla-

I've done some research on your intel gpu and will continue to look further. I would like for you to run these things to gather some more information. It is a good thing that you can get safe mode and I think we'll need to try some some kernel mode setting to get better results.

First, run this command.
```
/usr/lib/nux/unity_support_test -p
```Please post the results. I suspect this will tell us you can't run unity or unity 3d and if so that will tell us which environments to focus on. This command is from this link. [https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

I'd like to know just what happens during an attempt at a normal boot. When does it fail and how? Please see the first post in this thread if you need for troubleshooting the boot if needed. [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Post 1 of that thread is where the solution most likely lies. It shows a lot of information and not all of it is specific to Intel gpu's. It does go through the process of trying some kernel mode settings and does have some intel specific detail. Post 3 shows a way of making temporary kernel mode changes using the live cd and that can also be done from the grub menu.

I don't want to get to far ahead without knowing more of your specifics. That thread is real long and if you want to read more of it, go for it. There are other commands that can be run to get more information but let's try to stay organized and not do things not needed. The good thing is that you are in a better spot than many others using that thread. :D


Here's the result:

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no

At normal boot (9 times out of 10) I can hear the hard drive starting up and after about 15 seconds a white and light gray striped screen appears. Something is written in white in the middle but I can't decipher it. Mind you, I'm running an external Samsung monitor as the Panasonic monitor is cracked. The white screen turns off after 5 seconds. After 20 seconds I hear the Ubuntu 'jungle chime' so I guess it's booting but after that the monitor never turns on. Occasionally I'll get a menu in the beginning giving me boot options. I choose recovery mode (failsafe graphics) and that works. I can boot off the CD and I can get the menu if I hold down Shift.

---

### Post by bluetortilla on 2011-06-10
> **alphacrucis2 said:**
> I did find this on ubuntu geek. Seems that there is a launchpad PPA that may help but as the comment says use at own risk:

[http://www.ubuntugeek.com/how-to-install-intel-82852855gm-drivers-in-ubuntu-using-ppa.html](http://www.ubuntugeek.com/how-to-install-intel-82852855gm-drivers-in-ubuntu-using-ppa.html)

From what I gather the glasen ppa has bleeding edge intel drivers built from git.

Here's the direct link to the launhpad ppa if you want to have a look:

[https://launchpad.net/~glasen/+archive/intel-driver]("https://launchpad.net/%7Eglasen/+archive/intel-driver")

Thanks. My results were (truncated):

Fetched 254 kB in 5s (43.8 kB/s)
Reading package lists... Done
planet@Planet2:~$ sudo apt-get install xserver-xorg-video-intel 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

After running the script twice. So it appears these are the latest drivers. 

I seem to be having less boot issues, though why the problem remains intermittent I don't know. The other problem is that my configure display settings panel has not changed (unknown device). I cannot toggle off the laptop monitor, which is simply eating up RAM as it unreadable. 

I guess this is as good as it gets?

---

### Post by bluetortilla on 2011-06-10
> **Immolatus said:**
> you must manually edit xorg.conf to include this monitor if it's not automatically detected.

"screen" section.

intel gma drivers wont fix this or help you manipulate either.

Sorry. I tried this but couldn't find the 'screen' section. And even if I did, I have no idea about how to manually configure the drivers.

As you said, the intel drivers didn't do much of anything- it seems to boot more compliantly now but that's it.

??

Dummy, I admit it.... :)

---

### Post by Immolatus on 2011-06-10
No....this doesn't mean you're dumb. It's actually an interesting project. The "screen" section just might not have been generated on install. The best place to learn about xorg is the Xorg wiki. Also concerning configuration you might have a look at the Arch xorg wiki. Arch Linux requires extensive end user configuration so the documentation is stellar.

One more thought.....most lappies with an external VGA out require a key combination (fn + some hot-key) to function and some will just display on both until you specify.

---

### Post by bluetortilla on 2011-06-10
> **Immolatus said:**
> No....this doesn't mean you're dumb. It's actually an interesting project. The "screen" section just might not have been generated on install. The best place to learn about xorg is the Xorg wiki. Also concerning configuration you might have a look at the Arch xorg wiki. Arch Linux requires extensive end user configuration so the documentation is stellar .

I've tried to start at Xorg Wiki, but I'm stuck at the commands. What does the # sign mean? I can't get any response in Terminal:

planet@Planet2:~$ # pacman -Syu xorg-server 
planet@Planet2:~$ # pacman -Ss xf86-video
planet@Planet2:~$ 

I've looked up the # sign and it said #! works as a compatible prompter between different shells.


> **Immolatus said:**
> One more thought.....most lappies with an external VGA out require a key combination (fn + some hot-key) to function and some will just display on both until you specify.

Weird. Brightness works but toggling doesn't...

---

### Post by Immolatus on 2011-07-21
sorry I took so long to reply....
pacman is the Arch Linux package manager not Ubuntu(aptitude(apt)). what you really need is just a crash course in Xorg configuration for no specific distro.

---

