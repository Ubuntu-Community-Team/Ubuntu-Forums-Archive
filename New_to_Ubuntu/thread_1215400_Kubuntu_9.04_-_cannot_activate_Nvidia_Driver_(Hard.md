---
title: "Kubuntu 9.04 - cannot activate Nvidia Driver (Hardware Drivers)"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by manilaph on 2009-07-17
On "Hardware Drivers" in Kubuntu, it shows that I have to activate the Nvidia-96 driver but when I press the "activate" button... nothing happens at all.

I check the nvidia-settings and it says there are no nvidia drivers installed.

Everytime I start Kubuntu... I go back to 800x600 when it should 1024x768.

I am getting frustrated with Nvidia stuff.

---

### Post by Bartender on 2009-07-17
You do know that the PC has to be connected to the web to get the drivers, right?  The "Activate" button is a little misleading if taken out of context.  What it really does is download the driver, then install.  If no internet connection, the "activate" button does nothing.

---

### Post by NightwishFan on 2009-07-17
If in doubt install it manually and then do the activation. The package name is:

nvidia-glx-96

---

### Post by manilaph on 2009-07-17
thanks for the replies.

yes of course i am connected to the internet (wired).

i have also tried the 

apt-get install nvidia-glx-96

... but when i go to nvidia-settings (as root), the drivers cannot be found or there are no drivers

... but when i go to the restricted drivers "activate"... it says that there is already a version installed.

i have written about this on another thread too.

please note that i previously used ubuntu 9.04 and was able to solve the problem there and the "activate" nvidia drivers worked with ubuntu... then all i did was go to gksu and adjust the nvidia-settings to keep it permanent.

i just got attracted to KDE... it is beautiful but is seems that gnome is more functional really... and it just works.

---

### Post by Bartender on 2009-07-17
I want to like Kubuntu but have tried it several times and keep ending up back at Ubuntu.  Usually same reasons as you're stating - something that worked in Gnome stops working or doesn't seem to work as well in KDE.

---

### Post by manilaph on 2009-07-17
there are sooo many similar problems with Kubuntu
[http://ubuntuforums.org/showthread.php?t=1154145&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=1154145&highlight=nvidia)

what if i install ubuntu first and then install the KDE version... would that mess-up the "okay" nvidia-settings that I have in Ubuntu?

i have not yet found a KDE distro that would work well with Nvidia. some say that i should try Mepis 8.0 or Opensuse.

i have tried Mandriva and it too does not work (but the gnome version does).

i guess this is a KDE bug?

---

### Post by NightwishFan on 2009-07-18
Kubuntu is more solid than some give it credit for. Are you sure you need the 96 version driver? I have an old 6 series and I use the 185 version. I had some trouble with jockey-kde in the beta, however it works for me now.

Try this:

[LIST=1]
[*]Install the required Nvidia packages in Synaptic.
[*]Reboot.
[*]Open jockey-kde (hardware drivers) and try to activate.
[*]If yes (or no) reboot again.
[*]We can try to use jockey using commands, but we can get to that step.
[/LIST]

---

### Post by arochester on 2009-07-18
I think that the Activate Button can be misleading because it is S-L-O-W. Click it, keep it open and WAIT. Keep Waiting. And keep waiting. It should get there in the end. Then when it has loaded Reboot.

---

### Post by vertago1 on 2009-07-18
There is a bug in jockey-kde which prevented me from installing the driver so I installed jockey-gtk and was able to get it to work.

---

### Post by manilaph on 2009-07-19
Nightwishfan,

The reason why I know it is the Nvidia-96 driver is because that is what Ubuntu & Kubuntu recommended as a driver to install/activate.

Arochester,

How long should I wait after pressing the "activate" button to install the recommended nvidia-96 driver?

Vertago1,

I think you are correct.... I saw a brief flash of an error with the word "jockey"... I had no idea what it was.


Do you guys think I should try and re-install Kubuntu? I am currently using Ubuntu without any problems whatsoever. Everything just works flawlessly.

In my opinion, in terms of "good looks"... Kubuntu wins hands-down. But in terms of ease-of-use, Ubuntu has an advantage. More likely because I am more familiar with it.

What happens if I:
sudo apt-get install kubuntu-desktop (while using Ubuntu)?

Thanks guys!

---

### Post by Tr1bal on 2009-08-23
First off sorry for the necropost, but I'm having the same exact problem in Ubuntu 9.04. manilaph, you said you got in working when you still had Ubuntu? Could you possibly ellaborate how you did that?

Anybody who can help, thank you in advance.

---

### Post by inobe on 2009-08-23
> **Tr1bal said:**
> First off sorry for the necropost, but I'm having the same exact problem in Ubuntu 9.04. manilaph, you said you got in working when you still had Ubuntu? Could you possibly ellaborate how you did that?

Anybody who can help, thank you in advance.

tribal i will try to help, open terminal and type

```
lspci
```

then hit enter, copy and paste the output on next post.

---

### Post by Tr1bal on 2009-08-23
Sure thing.

```

$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 05)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 05)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
02:01.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:04.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
03:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)

```

---

### Post by inobe on 2009-08-23
i found this and will be looking into it

[http://www.nvnews.net/vbulletin/showthread.php?t=129124](http://www.nvnews.net/vbulletin/showthread.php?t=129124)

check back later

---

### Post by Tr1bal on 2009-08-23
I don't know if it makes a difference, but I'm using kernel 2.6.27-14-generic because I couln't get the 2.6.28 kernel to work. Thanks for all the help :)

---

### Post by inobe on 2009-08-23
i assume there are no proprietary drivers in use ?

open synaptic and type **nvidia**

list what is installed, you can do it screenshot if you don't wish to type.

i think your missing something.

---

### Post by Tr1bal on 2009-08-23
These are what show up as installed:

jockey-common
jockey-gtk
linux-restricted-modultes-2.6.24-16-generic
nvidia-173-modaliases
nvidia-180-modaliases
nvidia-71-modaliases
nvidia-96-kernel-source
nvidia-96-kernel-source
nvidia-common
nvidia-glx-96
nvidia-kernel-common
nvidia-settings
smartdimmer
xserver-xorg-video-nv

---

### Post by inobe on 2009-08-23
i believe the card will use the 71 driver !

i don't see the model listed....

[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-71/71.86.08-0ubuntu1](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-71/71.86.08-0ubuntu1)

to very the actual model' could i have the make and model of your pc, i would like to verify this before installing any drivers.

---

### Post by Tr1bal on 2009-08-23
Jockey says that the recommended driver is 96 but sure,

I am running a Dell Inspiron 2650 Laptop

---

### Post by inobe on 2009-08-23
we can do the 96, i noticed 96 modealias isn't listed, that needs to be installed.

i would install everything 96 besides the devs and reboot, upon rebooting check hardware drivers.

if for any reason you don't have video at all hit escape at the boot screen, choose recovery, choose xfix from the list.

---

### Post by Tr1bal on 2009-08-23
Everything 96 is already installed, and the 96 modalias is installed, I just accidently listed 'nvidia-96-kernel-source' twice >.< Sorry about that.

---

### Post by inobe on 2009-08-23
have you tried envyng ?


[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

it's an easy option' for many it has worked, for some it hasn't.



for the meantime i am guessing nvidia has slacked support for old hardware, this may be why video drivers are not in hardware drivers.

there is an option to edit xorg however you will not find the composite feature listed.

---

### Post by Tr1bal on 2009-08-23
At one point I did have EnvyNG installed, but I got an error when trying to enable the drivers.  So I un-installed because I didn't have a use for it anymore.

---

### Post by inobe on 2009-08-23
to bring up your xorg.conf in terminal.


```
sudo nano /etc/X11/xorg.conf
```


don't edit anything


here's mines

```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection


```

nothing there, completely empty, back in the days it was easier to edit this config, now it's back to school for me.

---

### Post by Tr1bal on 2009-08-23
Here's mine:
```

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals"    "True"
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```

---

### Post by inobe on 2009-08-23
if i find a way i will post it here and contact you.


till then i would dump everything installed for 96, reboot.

upon rebooting attempt to reinstall all of what you removed.

that's all i have for now.

---

### Post by Tr1bal on 2009-08-23
Ok, I tried what you said, even tried using envyNG before all else, and it still failed. In EnvyNG I get this error message:

```

[FONT=Courier New]+--------------------------------------------------------+
|    Error:                                              |
|                                                        |
|    EnvyNG has detected that the headers for            |
|    your kernel are missing and cannot be installed     |
|                                                        |
+--------------------------------------------------------+[/FONT]

```

So I went into System->Administration->Hardware Drivers and tried to activate it again, everything seems to be working, it downloads/installs the drivers, but the driver is still not activated.

---

### Post by inobe on 2009-08-24
the headers are "build essentials"

in terminal, type

```
sudo apt-get install build-essential
```

---

### Post by Tr1bal on 2009-08-24
It's already installed, installed it for my programming needs.

---

### Post by inobe on 2009-08-24
good grief :lol:

edit: can someone join in and kindly explain what the heck is gone wrong ?

---

### Post by manilaph on 2009-08-24
hi,

if this is a new installation, i would suggest another fresh installation.

my "need" for proprietary drivers (Nvidia) was automatically detected using Ubuntu and it gave me an option to "activate" these drivers.

I did not use synaptic to install these drivers.

---

### Post by Tr1bal on 2009-08-24
Ah, that helps, kinda.

That might not be possible in my situation since I upgraded through 8.04 to 9.04(No way to burn disks :()

Thanks for all the help though, and sorry for hijacking your topic manilaph :)

---

### Post by Perfect Storm on 2009-08-24
> **Tr1bal said:**
> Ah, that helps, kinda.

That might not be possible in my situation since I upgraded through 8.04 to 9.04(No way to burn disks :()

Thanks for all the help though, and sorry for hijacking your topic manilaph :)

If you have an USB stick you can do it though there (if your computer support USB bootup.)

---

### Post by Tr1bal on 2009-08-24
I tried that but my computer is to old, even tried through grub, but no luck...

---

### Post by simpar on 2009-12-15
Getting back to the original question, 
[INDENT][I]
On "Hardware Drivers" in Kubuntu, it shows that I have to activate the
Nvidia-96 driver but when I press the "activate" button... nothing 
happens at all.[/I][/INDENT]

I recently install Kubuntu 9.10 on two different PCs and was faced with the same problem in both cases, ie pressing the Activate button does nothing. After some research and some more 'random' button pressing I managed to get the activate button to work. How did I do this? When I start up the Hardware Drivers app, I am presented with two drivers 173 and 185, if I try to activate 173, nothing happens, if I try to select 185 then all is good (ie it can be activated). Furthermore, once I try to activate the 173 (which doesn't work) I cant get the 185 to work. 

So in summary what worked FOR ME was:
1. Starting Hardware Drivers
2. Selecting Version 185
3. Pressing Activate
And pretty much straight away (ie no long waits) the installation process started.

Hope this helps.

---

### Post by manilaph on 2009-12-16
Thank you very much for your reply and tutorial. It is much appreciated.

I have since moved over to Xubuntu 9.10 which I find to be very fast and intuitive as compared to Kubuntu 9.10.

Cheers!

---

