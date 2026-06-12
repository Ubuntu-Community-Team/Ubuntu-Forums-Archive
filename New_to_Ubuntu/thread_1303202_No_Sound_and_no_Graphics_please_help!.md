---
title: "No Sound and no Graphics please help!"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by Earl-Grey on 2009-10-28
[FONT=Tahoma][SIZE=2]I am using the latest version of Ubuntu and apart from the above problem I think it is great. 

I've been trying for quite a few days to find a driver for my sound card and graphics card but no luck as of yet.  

For my audio settings I have tried the obvious, to see if my sound is muted but it seems to be fine. Also followed the instructions on this thread `http://ubuntuforums.org/showthread.php?t=205449` but still no sound.  

My graphic settings aren't that bad as I can still view my desktop and play a few basic games, but I am not able to render 3D as far as I know. I can not play the 3D chess game this build comes with and I can't change my  visual effects to Normal, Extra or Custom. It simply says `Desktop effects could not be enabled`.  
[B]
_Audio_  [/B]

In XP my audio device is called `SoundMax Intergrated Digital Audio` but when I type in **aplay -l** to the terminal I get this information;  
[/SIZE][/FONT][INDENT][FONT=Tahoma][SIZE=2]card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]  
Subdevices: 0/1  
Subdevice #0: subdevice #0  
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]  Subdevices: 0/1 
Subdevice #0: subdevice #0  
[/SIZE][/FONT] [/INDENT][FONT=Tahoma][SIZE=2]This is what I get when I type** lspci -v**;  
[/SIZE][/FONT][INDENT][FONT=Tahoma][size=2]00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
Subsystem: NEC Corporation Device 82bd  
Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17  
Memory at c0003400 (32-bit, non-prefetchable) [SIZE=256]  
[SIZE=2]Capabilities:  Kernel driver in use: ATI IXP AC97 controller  
Kernel modules: snd-atiixp   [/SIZE]
[/SIZE][/FONT] [/INDENT][FONT=Tahoma][SIZE=2]_**Graphics**_

My graphics card is an ATI Radeon Xpress 200M Series and this is the information I get from  **lspci -v**;

[/SIZE][/FONT][INDENT][FONT=Tahoma][SIZE=2]01:05.0 VGA compatible controller: ATI Technologies Inc RS400 [Radeon Xpress 200M] Subsystem: NEC Corporation Device 82c8[/SIZE][/FONT]
[FONT=Tahoma][SIZE=2]Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 17 [/SIZE][/FONT]
[FONT=Tahoma][SIZE=2]Memory at d0000000 (32-bit, prefetchable) [size=256M] [/SIZE][/FONT]
[FONT=Tahoma][size=2]I/O ports at 9000 [/FONT]
[FONT=Tahoma][SIZE=2]Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
[virtual] Expansion ROM at c0120000 [disabled] [size=128K] [/SIZE][/FONT]
[FONT=Tahoma][SIZE=2]Capabilities: <access denied>[/SIZE][/FONT]
[FONT=Tahoma][SIZE=2]Kernel modules: radeon   [/SIZE][/FONT]
[/INDENT][FONT=Tahoma][SIZE=2]

Any help would be much appreciated.[/SIZE][/FONT]

---

### Post by hellblazer on 2009-10-28
I can't help with the sound issues, but as for the graphics problems you need to install a 3rd party driver to get 3D acceleration.

On your menu at the top left go to System > Administration > Hardware Drivers

The app will search for the appropriate drivers for your card and recommend one.

This doesn;t always work, but it's a good place to start.

---

### Post by danielkabrinski on 2009-10-28
In the package manager try installing Alsa.  If it is installed, reinstall it.  I had a sound issue like this and reinstalling worked for me.

---

### Post by ublintu on 2009-10-28
I have the same graphic card, ati 200m.
In 9.04 I found this links (none of them is the perfect solution and be careful, when you will try them):
[http://ubuntu-ky.ubuntuforums.org/sh....php?p=7733415](http://ubuntu-ky.ubuntuforums.org/sh....php?p=7733415)
[http://friendlytechninja.vndv.com/20...driver-issues/](http://friendlytechninja.vndv.com/20...driver-issues/) 
[http://ubuntuforums.org/showthread.p...ss+200M&page=5](http://ubuntuforums.org/showthread.p...ss+200M&page=5)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[http://ubuntuforums.org/showthread.p...n+x1100&page=4](http://ubuntuforums.org/showthread.p...n+x1100&page=4)
Back up all of your data first!!!
Just 1 more day and 9.10 is out. Hopefully it will be better 4 us...

---

### Post by Mark Phelps on 2009-10-28
Earl-Grey: 

I presume by "latest" you mean 9.04, but the sad news is, there is no ATI driver for your card that works with 9.04 or newer. Thus, you won't be offered anything in Hardware Drivers.

Do NOT download the ATI driver and try to force the installation.  If you do, you'll corrupt your display setup and will be forced to boot into a console to remove the ATI drivers and restore the open source drivers.

Since you're getting a desktop, you already have the open source drivers installed -- which are the best you will get.

---

### Post by Earl-Grey on 2009-10-28
> **ublintu said:**
> I have the same graphic card, ati 200m.
In 9.04 I found this links (none of them is the perfect solution and be careful, when you will try them):
[http://ubuntu-ky.ubuntuforums.org/sh....php?p=7733415](http://ubuntu-ky.ubuntuforums.org/sh....php?p=7733415)
[http://friendlytechninja.vndv.com/20...driver-issues/](http://friendlytechninja.vndv.com/20...driver-issues/) 
[http://ubuntuforums.org/showthread.p...ss+200M&page=5](http://ubuntuforums.org/showthread.p...ss+200M&page=5)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[http://ubuntuforums.org/showthread.p...n+x1100&page=4](http://ubuntuforums.org/showthread.p...n+x1100&page=4)
Back up all of your data first!!!
Just 1 more day and 9.10 is out. Hopefully it will be better 4 us...


Just wanted to say thank you very much to everybody who offered their advice :p

All I did was follow this information; 

**Removing the proprietary fglrx driver**
[INDENT]*fglrx* is the name of the closed-source, proprietary driver from ATI. It conflicts with the open-source "radeon" driver. If the "fglrx" kernel module is loaded at boot, X will be able to start using the "radeon" driver but "Direct Rendering" (DRI) will be disabled. This results in a severe performance reduction. Use System->Administration->Hardware Drivers to make sure "ATI accelerated graphics driver" is not in use. 
It is important to note that with the release of 9.04, the fglrx driver dropped support for the r500 line of cards. If you are upgrading from 8.10 or a previous release and use one of these cards, it is strongly suggested that you remove fglrx prior to upgrading to avoid any problems. However, you can still remove the fglrx driver after the upgrade if it causes problems. 
If you previously used the proprietary "fglrx" driver it is highly recommended to totally get rid of the fglrx package: 
```
$ sudo apt-get remove --purge xorg-driver-fglrx
```and reboot the computer. 
The libGL.so in /usr/lib might also still be the version installed by xorg-driver-fglrx. You can check that very easily, just run: 

```
$ glxinfo |grep vendor
```If you see: client glx vendor string: ATI, then the libGL.so is still from ATI.  
Make sure libgl1-mesa-glx and libgl1-mesa-dri are properly installed:```

$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
```Make sure "fglrx" is not listed in /etc/modules file.   
Of course, make sure your xorg.conf does not contain any "fglrx" entry.
[/INDENT]From the [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) page and now my graphics work fine. I can also view the 3D cube and groovy visual effects :KS 

Just got to get some sound and I'm sorted.

Thank you again

---

### Post by ublintu on 2009-10-28
I`m happy, because it`s working now

---

### Post by Earl-Grey on 2009-10-29
I found this information out about my sound card, but still no luck. If I manage to get it working I will post how I did it here.

[http://ubuntuforums.org/archive/index.php/t-365342.html](http://ubuntuforums.org/archive/index.php/t-365342.html)

Can't believe that I got it to work.

I read this message;

 				 				**Re: Sound card problems - ATI Technologies Inc IXP SB400 AC'97 Audio Controller** 			
 			 			 		   		 		 		Sorry, now in english:

add to /etc/modprobe.d/options the line(s)

# for soundchip snd_atiixp
options snd-atiixp ac97_codec=0

and restart the system. Hope it helps.

From this thread &#8594; [http://ubuntuforums.org/showthread.php?t=365342&page=2](http://ubuntuforums.org/showthread.php?t=365342&page=2)


I did try a lot of things, so it might be an accumulation of all the this I did and not just this latter part.

---

