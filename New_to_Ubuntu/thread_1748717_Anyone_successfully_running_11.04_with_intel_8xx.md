---
title: "Anyone successfully running 11.04 with intel 8xx?"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by migrate from windows on 2011-05-03
Anyone successfully running 11.04 with intel 8xx? ( my video hradware is Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

Does unity desktop work in it?

Just wanna make sure b4 taking the big step!!

---

### Post by 3rdalbum on 2011-05-03
Making sure before taking the big step of trying out Unity on a live CD? :-P

If Compiz runs, then Unity should be fine. But as I said, you can try out the live CD.

---

### Post by migrate from windows on 2011-05-03
Thanx, but doesnt live cd just use the generic drivers? or is it no different from an installation, does compiz run in live cd?

---

### Post by 3rdalbum on 2011-05-03
With Intel drivers, the official ones are included on the Ubuntu CD because they are open-source.

---

### Post by migrate from windows on 2011-05-04
Still I would love to hear from anybody who has successfully upgraded with intel i8xx!

---

### Post by deckoff on 2011-05-05
I'd rather try the Clonezilla method - back up the whole system - and upgrade. I did so. I have better results with 10.10 , Kubuntu, and the newest driver installed. 
I tried with several different kernels, system is usable, but if OpenGL is enable I got more than enough bugs. I will stick with 10.10 for now and wait for bug fixes. 
Hope it helps

---

### Post by migrate from windows on 2011-05-12
> **deckoff said:**
> I'd rather try the Clonezilla method .......Hope it helps
Thanx thats a good idea!

---

### Post by Rubi1200 on 2011-05-12
> **migrate from windows said:**
> Anyone successfully running 11.04 with intel 8xx? ( my video hradware is Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

Does unity desktop work in it?

Just wanna make sure b4 taking the big step!!
I am using 11.04 on a test partition with Intel i8xx graphics and this is a brief summary of my experiences thus far:

1. 11.04 does not work out of the box with this series of Intel chipsets (this also according to Stefan Glasenhardt who packaged the PPA fixes for 10.04 and 10.10)

2. if you install, you will probably not be able to run regular 3D Unity and will be dropped to the Classic desktop after installing

Possible solutions:

1. you need to create a xorg configuration file to deal with the fact that the fbdev driver defaults at installation time:

```
gksudo gedit /etc/X11/xorg.conf

```
This creates an empty file; paste the following into the file and save:

> Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

2. you can install Unity-2D via Synaptic. It works nicely on my machine, but it is not as configurable as regular Unity. I believe it is being developed for the next release though.

There is an experimental 3D driver available for the Intel chipsets in question, but I have not tested this.

Hope this proves useful to you.

---

### Post by migrate from windows on 2011-05-13
Thnx Ruby1200! Do u experience any freezes or blackscreens?

---

### Post by Rubi1200 on 2011-05-13
> **migrate from windows said:**
> Thnx Ruby1200! Do u experience any freezes or blackscreens?
Not on my machine, at least not with the workarounds I have applied so far. I did experience some other oddities, but I think those are related to other issues and not the chipset itself.

If you are having a problem with black/blank screens you might want to try adding i915.modeset to grub and see if it helps (this can be undone later if it has little/no effect):

```
gksudo gedit /etc/default/grub
```

change this line:
>  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

so it looks like this:
>  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"

Close and save then run this in the terminal:
```
sudo update-grub
```

I don't know of other "fixes" at this time that can help, but I hope this gets you somewhere with using 11.04. If not, you may have to wait until 11.10 comes out and see if some of these issues have been resolved.

---

### Post by rodnitski on 2011-05-18
[QUOTE/]
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1" 
[/QUOTE]
 
this did not work for me...HOWEVER changing the line to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
 
did work for me but now I get a white "test pattern' of lines or fence boards before the desktop occurs and works correctly after that

---

### Post by Dexter_Greycells on 2011-05-23
Yes, my 6 yr old desktop has an Intel 845 motherboard on it and I have installed Ubuntu 11.04 just yesterday. The Live CD just ran GNOME, not Unity which is kind of what I expected. After installation and at first login it told me that my graphics were not powerful enough to run Unity (3D) and hence Ubuntu will default to the GNOME interface. 

The GNOME interface felt really lively (I guess it is because of the 2.6.38 kernel) but I just had to have Unity. So I installed Unity 2D (sudo apt-get install unity-2d) but can't get it to work. It is displaying just the desktop and desktop icons with no panel or launcher or dash.

When I try to launch them from the terminal I get an error that points to some undefined symbols and Qt libraries. I installed a supposedly bad package prior to that which might explain that problem. Searching for a fix in ubuntuforums right now ;-)

So, if you are looking for the GNOME interface, go on and install 11.04 without worrying. Unity 3D is not supported and Unity 2D might require some work.

---

### Post by migrate from windows on 2011-05-24
Thanks dexter your reply will help me decide.

---

### Post by Ni-el on 2011-05-28
Just a quick note. The "xserver-xorg-video-intel" driver in 10.10 is 2.12. The new version is 2.14 and that seems to be the problem, because I ran into the same issue with the 2.14 driver in the new Fedora. 
I did get the debian 2.12 driver from launchpad at: [https://launchpad.net/ubuntu/maverick/i386/xserver-xorg-video-intel/2:2.12.0-1ubuntu5.2](https://launchpad.net/ubuntu/maverick/i386/xserver-xorg-video-intel/2:2.12.0-1ubuntu5.2).  Haven't tried to do it yet...

---

### Post by migrate from windows on 2011-05-28
@Ni-el pls post after you give it a try.

---

### Post by Ni-el on 2011-05-29
Didn't do it yet, but what I did do that didn't work was to try to install the .deb for xserver-org-video-intel version 2.15 that came out latest. What it said when I tried was that it would break the current version so it wouldn't let me do it. Next week *I'll take the plunge after I back up the important stuff because I only have the one machine with the Intel graphics.*

---

### Post by Ni-el on 2011-05-29
My latest step was to upgrade to Natty through the upgrade manager. Everything was fine except for this same screen size problem, as expected. Went in to Monitors and disabled the "Unknown" monitor (VGA1) and set the "Laptop" monitor (LVDS1) to 1400x1050, which is the closest one that fills the screen because of the 2cm space on the right. This is all as before. Secondly, I added the xorg-edgers repository from Launchpad at: [https://launchpad.net/~xorg-edgers/+archive/ppa/+index?start=225&batch=75](https://launchpad.net/~xorg-edgers/+archive/ppa/+index?start=225&batch=75) (be sure to read the whole page first). This allowed me to upgrade all of the xorg drivers. I now have xserver-xorg-video-intel v.2.15._ It hasn't changed the framing problem._  BUT, if you read the important notice on that page you will see "Updates for releases before natty are no longer planned due to drastic changes in the build systems". That makes me think that there is a problem beyond the drivers, so I will keep looking into why the frame is being limited. Anybody else think of another approach?

---

### Post by Ni-el on 2011-05-29
UPDATE -- Well I'm not getting anywhere with this. My display is a 16:10 ratio, but according to an industry report, nobody is making these any more. Now 16:9 or 4:3 is the standard. I can change the resolution to 16:10, but because the screen isn't being detected at 16:10 that resolution is the wrong shape. It is a detection issue bit I can't get an answer on how to force it. It just looks like there aren't enough of these monitors around and nobody seems to be working on this problem, so I'l just wait until it gets fixed or I buy a different computer. Sorry, that's as much as I can do for now.

---

### Post by jcolyn on 2011-05-29
I never had any luck so instead I installed Kubuntu. KDE does not have issues with the 8xxx intel..

---

### Post by Ni-el on 2011-06-08
That's not entirely true, though. I tried the latest Suse and Fedora15 with KDE and had this same problem with both, so KDE is not a factor. I did, however try Mandriva with KDE and it is great looking and fully configurable. Here is my final choice though. I installed the latest Debian (Squeeze) in Gnome flavour, then added the KDE4 desktop. I love it (so far), it has the graphics, the apps, and controls to do everything I want. This is one time that KDE has beat Gnome, and Debian lets the user decide what they want to put in or leave out.

---

### Post by praveenkumarjayaram on 2011-08-11
Ubuntu 11.10 Aplha 3 seems to work considerably good on Intel 8XX boards :)
I have 865GvHZ and it works good (though the windows are not rendered completely sometimes).

I have raised a bug too: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/823136](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/823136)

Hope this would be resolved completely in the final release.

---

