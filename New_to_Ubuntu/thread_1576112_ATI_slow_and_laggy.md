---
title: "ATI slow and laggy"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by Ballbrekr on 2010-09-16
This is my very first post...

I have an AMD phenom X4 processor, ATI radeon HD 5770, 8Gb of RAM.  (if you need more intel please let me know)

Some background:
     2weeks into Ubuntu (love it, even though im noob)
     No dual boot system
     Using UBUNTU 10.04 and the drivers suggested(FGLRX) by it for my video card (maybe thats 
     the problem, dont know)

Description of the issue:
     Everything visually is slow and laggy.  I have installed WINE (to play world of warcraft on)
I get anywhere from 3 - 10 frames per second on warcraft.  I have looked at (i think) every post about running the game in linux. 

I really do not want to give up on Linux.  This is pretty much my last resort.  I have glxinfo | grep rendering
that says yes its enabled
The game launches fine I can log in and I can move.  I have openGL set.  Do I need to go out and buy a new video card?  Is it something in my software, something in my drivers?     

Is that framerate the best I can do?  Is there anything better than WINE?  Do I need to setup up my video drivers in Wine somehow?  

Someone please respond with any information you may think is necessary for me.

Very Respectfully,
Ballbrekr

---

### Post by flick on 2010-09-16
By "Everything visually is slow and laggy." do you mean everything : web browsing, editing photos, opening a text editor?

Or do you mean 3D gaming is slow and laggy, but everything else is fine?

IF it's the latter, try turning off desktop effects before starting up a game. Sometimes Compiz/desktop effects don't play nicely with 3D games.

System > Preferences > Appearance > Visual Effects tab > None.

---

### Post by Ballbrekr on 2010-09-16
I should have been more specific.  Everything is slow and laggy.  2d and 3d materials.  Web browsing even calling up firefox is slow. I will also turn off all compiz software so we can get to basics again. Thank you for your prompt reply :)

Very Respectfully,
Ballbrekr

---

### Post by flick on 2010-09-16
OK, so everything is slow and laggy. I can certainly understand your frustration. Has it been like this for the full two weeks you've been using Ubuntu, or was there a time when it seemed fine, then became slow and laggy? I'm wondering if a recent update to the kernel, xorg, or your video driver might have caused an issue.

---

### Post by ubunterooster on 2010-09-16
press ctrl+Shift+t to bring up the terminal. write "top" 

What is the free RAM?

---

### Post by chaanakya_chiraag on 2010-09-16
I believe ctrl+shift+t is your custom keyboard shortcut ;)
Go to Applications->Accessories->Terminal and type ```
top
```
Please post your results here.

---

### Post by chaanakya_chiraag on 2010-09-16
Another command (which would display the same information more concisely) is ```
free -m
```

---

### Post by fancypiper on 2010-09-16
To find out what your video card is, open an x terminal and examine the results of the command:

sudo lshw | less

Scroll down to **display** and report back.

---

### Post by flick on 2010-09-16
Looks like the 5770 card is not especially well supported in Lucid Lynx just yet :

[http://ubuntuforums.org/showthread.php?t=1463961&page=4](http://ubuntuforums.org/showthread.php?t=1463961&page=4)

---

### Post by Ballbrekr on 2010-09-16
The lagging started when I started messing around with the video drivers.  The first time was before the reinstall of UBUNTU and same thing after second install. (thought i screwed up something.)

Ok so "top" results:
     Mem:  8195084K total,  3128664K used,  5066544K free

The other command produced these results: no idea how to read them.

description: Desktop Computer
    product: DX4200-09
    vendor: Gateway
    version: 7B3P091G
    serial: XXXXXXXXXXXXXXXXXX
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=0022684B-2090-2009-0307-195843000000
  *-core
       description: Motherboard
       product: RS780
       vendor: Gateway
       physical id: 0
       version: Rev 1.0
       serial: xxxxxxxxxxx
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 7B3P091G (08/06/2008)

Hope that stuff helped us :)

Very Respectfully,
Ball

---

### Post by Ballbrekr on 2010-09-16
sorry forgot the scroll down part:

*-display
                description: VGA compatible controller
                product: Juniper [Radeon HD 5700 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:29 memory:d0000000-dfffffff(prefetchable) memory:fe9e0000-fe9fffff ioport:c000(size=256) memory:fe9c0000-fe9dffff(prefetchable)

---

### Post by flick on 2010-09-16
Do you happen to remember what you did when you were "messing around with the video drivers." ?

---

### Post by fancypiper on 2010-09-16
A quick and easy fix is to install a graphics card that supports Linux.  I have had good luck with nVidia cards.

My video card:
*-display
             description: VGA compatible controller
             product: G70 [GeForce 7800 GT]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:05:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:18 memory:fb000000-fbffffff memory:d0000000-dfffffff memory:fc000000-fcffffff ioport:6c00(size=128) memory:fd000000-fd01ffff

---

### Post by alphacrucis2 on 2010-09-16
> **Ballbrekr said:**
> sorry forgot the scroll down part:

*-display
                description: VGA compatible controller
                product: Juniper [Radeon HD 5700 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:29 memory:d0000000-dfffffff(prefetchable) memory:fe9e0000-fe9fffff ioport:c000(size=256) memory:fe9c0000-fe9dffff(prefetchable)

Which version of fglrx are you using? AMD just released Catalyst 10.9 yesterday. I have tested it out and it works very well. I would suggest downloading it and trying it out.

---

### Post by Ballbrekr on 2010-09-16
Just to install Mesa and the fglrx drivers from hardware update.    Also, I read the post
**ATI Radeon HD 5770 support by ubuntu 10.04?**  I wonder if i should try my other video card.  ATI radeon hd 4650.  Or just use the on board video  radeon HD 3200.  That or make a run to the nearest hardware store for an Nvidia graphics card ( any recomendations)?

Thank you for your time.

Very Respectfully,
Ball

---

### Post by Ballbrekr on 2010-09-16
> **alphacrucis2 said:**
> Which version of fglrx are you using? AMD just released Catalyst 10.9 yesterday. I have tested it out and it works very well. I would suggest downloading it and trying it out.

That sounds great. any chance you would be willing to share some knowledge about uninstalling this current driver and installing the one you are using?

Very Respectfully,
Ball

---

### Post by Ballbrekr on 2010-09-16
Thank you for showing me ctrl +shift + t for the terminal.

---

### Post by alphacrucis2 on 2010-09-16
> **Ballbrekr said:**
> That sounds great. any chance you would be willing to share some knowledge about uninstalling this current driver and installing the one you are using?

Very Respectfully,
Ball

1. Go to AMD website and enter your exact card model Radeon 5770 or whatever in the dropdowns, select linux 32 or 64 (depending on which you are running. It will list the available drivers for your card. Download the offered installer and also download the installer instructions pdf file. 

2. Erase the existing fglrx. 

Purge it from synaptic

```
sudo apt-get remove --purge fglrx*
``` 

I find that isn't enough to properly get rid of it. You should also run the ati uninstaller:

```
cd /user/share/ati
sudo sh ./fglrx-uninstall.sh
```

This might get some errors (because fglrx has already been removed by the apt-get remove but this step seems to get rid of some other junk that would otherwise trip on the install.

[COLOR="Red"]**WARNING DO NOT REBOOT NOW UNTIL you have COMPLETED step 3**[/COLOR]

Step 3. 

I would suggest creating a new folder called ati. Copy or move the installer you download from ati into the new ati folder. Then from a terminal session:


```
[COLOR="Lime"]cd ati[/COLOR]
sudo sh ./ati-driver-installer-10-9-x86.x86_64.run --buildpkg Ubuntu/lucid

```

Note that the above is for 64 bit. If you are running 32 bit, then the installer name (the file you downloaded will have a slightly different name). Also cd ati means to change the current dir to whereever you put the installer.

If the above works correctly, it will create a number of deb packages which you must now do a bulk install:

```
sudo dpkg -i *.deb
```

I seem to have trouble sometimes even though this appears to work but may not set things up quite right, so I strongly recommend also directly installing via the ATI method. Seems stupid but there it is (again assuming 64 bit):

```
sudo sh ./ati-driver-installer-10-9-x86.x86_64.run
```

Select the install driver option when it asks and agree to the licence.

Once installed [COLOR="Red"]**EXTREMELY IMPORTANT**[/COLOR] - enter this command before rebooting:

```
sudo aticonfig --initial -f
```

---

### Post by mastablasta on 2010-09-17
> **Ballbrekr said:**
> 
 
Ok so "top" results:
Mem: 8195084K total, 3128664K used, 5066544K free
 

 
can i also ask what kind of process you have running that takes those 3 GB of ram? it might be that they are slowing down computer performance especially during games. I mean 3GB is a lot. my Windows never go so high up, let alone (noncompiz) ubuntu that runs with <130 MB while idle.

---

### Post by chaanakya_chiraag on 2010-09-17
> **mastablasta said:**
> can i also ask what kind of process you have running that takes those 3 GB of ram? it might be that they are slowing down computer performance especially during games. I mean 3GB is a lot. my Windows never go so high up, let alone (noncompiz) ubuntu that runs with <130 MB while idle.
I am pretty sure ```
free -m
``` shows the cached RAM as "used"...not sure though...

---

### Post by Ballbrekr on 2010-09-18
Ladies and gentlemen,

I wish to thank all of you for your support in trying to help me with my issue.  I have purchased a newer nvidia card.  Although this card is also a little laggy and I do not get the framerates I should be getting, I think I am to much of a "noob" to fully grasp the workings of 3d video acceleration for the ATI cards.  Hopefully some day a more user friendly install will be available for ATI Radeon HD 5770.  I really prefer this to nvidia, I just gave up the fight (not really like me).  I am also wondering at this time if there is a gamer friendly distro of linux out there that may be more suitable for me (games, internet, and office apps.).  I will not be going back to windows that i can see at this time.  Actually, with nvidia still slow and laggy but faster than the ATI card, now im kinda wondering if there is an underlying problem here that i am not seeing.  What do you guys think?

Very Respectfully,
Ball

---

### Post by realzippy on 2010-09-18
..have you installed the NVIDIA driver offered in System/Administration/Hardwaredrivers?

---

### Post by Ballbrekr on 2010-09-18
Yes I did.  For some reason, I am unable to install the downloaded drivers from nvidia website.  tells me there is an x server running and not able to install in just text mode(not that good yet).

Very Respectfully,
Ball

---

### Post by realzippy on 2010-09-18
*Actually, with nvidia still slow and laggy*

..is the driver installed correctly?can you open a terminal,paste this:

```
glxinfo | grep OpenGL
```

and post it's ouput?

---

### Post by fancypiper on 2010-09-18
Try installing the driver from the menu **Administration > Hardware drivers**

---

### Post by realzippy on 2010-09-18
> **fancypiper said:**
> Try installing the driver from the menu **Administration > Hardware drivers**

...you read post #22 and #23 ?

---

### Post by fancypiper on 2010-09-18
> **realzippy said:**
> ...you read post #22 and #23 ?

I missed them.

---

### Post by Ballbrekr on 2010-09-18
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GT 240/PCI/SSE2
OpenGL version string: 3.2.0 NVIDIA 195.36.24
OpenGL shading language version string: 1.50 NVIDIA via Cg compiler
OpenGL extensions:


sorry for the delay there guys.  I also ran a benchmark.  With the ubuntu updated drivers my score was 476 "not good" got average of 16frames per second.  Anyone have any thoughts or suggestions?

Ball

---

### Post by realzippy on 2010-09-19
Output is fine.Which benchmark did you run?
Try another driver,the 260.xx ...
Did you uninstall the ATI driver stuff?
(Have you used the ATI FGLRX driver formerly)?

Post the nvidia-bug report,run:

```
sudo nvidia-bug-report.sh
```
(creates bug-report in your home directory)

---

### Post by Ballbrekr on 2010-09-24
Ok guys (and gals),

I have in my infinite wisdom (lol) decided to go back to my higher end video card, the ati radeon hd5770.  I put a fresh install of Ubuntu 10.04 am currently using the linux recommended driver for it.  The only thing that I have is compiz (finally got the cube to work...woot!!!) and cheese installed.  Having said that here is my results:

glxinfo | grep OpenGL
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5700 Series
OpenGL version string: 3.2.9756 Compatibility Profile Context
OpenGL shading language version string: 1.50
OpenGL extensions:


I get around 13k frames in glxgears
also scored a 1257 in unigine benchmark "tropical"

The only thing I can think of that I did differently was mess around with the custom setting in catalyst, i disabled the catalyst A.I.  thats about it.  Does anyone know if this is an actual fix or am i shooting myself in the foot doing that?

Thank you for your time.
Very Respectfully,
Ball

P.S.  If this works I think I still have time left to return the nvidia card :)

---

