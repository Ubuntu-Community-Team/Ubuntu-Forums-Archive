---
title: "Ubuntu 8.10 Screen Resolution Issues"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by Chris Hwang on 2009-01-14
Hello-

I seem to have a problem with my screen's resolution. The highest option allowed is 800x600, while the screen is capable of much higher resolutions.
I just installed ubuntu 8.10, and I tried editing xconfig. Any suggestions? 

Here is the video card:

01:00.0 VGA compatible controller: ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)] (rev 01)

And the laptop is a Sony S150...

Please help... :(

e-mail [email]chrishwang2005@hotmail.com[/email]

Thank You!

---

### Post by Jeyaganeshdj on 2009-01-14
Hi,

           Seems you have not installed the driver for your display. Go to System --> Administration --> Hardware Drivers and it will show you the available display drivers. Just click on the activate and your display driver should be activated.

---

### Post by northern lights on 2009-01-14
> **Jeyaganeshdj said:**
> Hi,

           Seems you have not installed the driver for your display. Go to System --> Administration --> Hardware Drivers and it will show you the available display drivers. Just click on the activate and your display driver should be activated.
If this does not fix the situation, please post the output of```
sudo lshw -C display
```
Thank you.

---

### Post by Chris Hwang on 2009-01-14
*-display UNCLAIMED     
       description: VGA compatible controller
       product: M9+ 5C61 [Radeon Mobility 9200 (AGP)]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm cap_list
       configuration: latency=66 mingnt=8

---

### Post by northern lights on 2009-01-14
Your device is not assigned a correct driver.

What release are you on?

AFAIK, a driver should appear under "System > Administration > Hardware Drivers".

Anyhow, run```
sudo apt-get install xorg-driver-fglrx
```Reboot. Now what?

---

### Post by Chris Hwang on 2009-01-14
8.10 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xorg-driver-fglrx

---

### Post by kansasnoob on 2009-01-14
Read here:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

> The model of the card is in the 9xxx series, 9500 or higher, or it is in the X series (e.g. X300), or it has TV-Out capability. The 'fglrx' driver does not support cards earlier than the 9500.

So I don't think fglrx fits your needs.

Now, I realize that only covers things thru 8.04! I'll try and do some more studying!

Xorg  has changed a lot!

---

### Post by kansasnoob on 2009-01-14
Ah, this looks promising, but read carefully!

I've not personally done any testing because I don't have any ATI to test!

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

---

### Post by northern lights on 2009-01-14
> **kansasnoob said:**
> So I don't think fglrx fits your needs.

Now, I realize that only covers things thru 8.04! I'll try and do some more studying!

Xorg  has changed a lot!

[QUOTE=Details of package: xorg-driver-fglrx (2:8.543-0ubuntu4) {restricted}]Video driver for the ATI Radeon and FireGL graphics accelerators.

This version of the ATI driver officially supports:

 * RADEON X1300, X1600, X1800, X1900
 * RADEON 8500, 9000, 9100, 9200, 9500, 9550, 9600, 9700, 9800
 * RADEON X800, X700, X600, X550, X300 series (AGP and PCI Express)
 * [COLOR="Red"]MOBILITY RADEON[/COLOR] 9000, [COLOR="Red"]9200[/COLOR], 9600, 9800, X700
 * MOBILITY RADEON 9000/9100 IGP Series
 * FireGL 8700, 8800, E1, E2, X1, X2, X3, Z1, T2
 * MOBILITY FireGL 9100, T2
 * RADEON XPRESS 200

. This package provides 2D display drivers and hardware accelerated OpenGL.[/QUOTE]

[http://packages.ubuntu.com/intrepid/xorg-driver-fglrx]("http://packages.ubuntu.com/intrepid/xorg-driver-fglrx")

@the OP:
What repositories do you have enabled/disabled?

---

### Post by Chris Hwang on 2009-01-14
Ok... What do I do now? I went to the website and downloaded the two files to my desktop... i'm a beginner to ubuntu and linux. Can anyone help me with a step by step process?

---

### Post by avtolle on 2009-01-14
I think what you should try is to enable the restricted repository under System>Administration>Software Sources, by checking the box beside Restricted; close out, you will get an onscreen message about reloading, reload, then after that is finished, instally the subject package through Synaptic.

---

### Post by Chris Hwang on 2009-01-14
sigh... why is this so complicated? still doesn't work

---

### Post by Slowspeed on 2009-01-14
> **avtolle said:**
> I think what you should try is to enable the restricted repository under System>Administration>Software Sources, by checking the box beside Restricted; close out, you will get an onscreen message about reloading, reload, then after that is finished, instally the subject package through Synaptic.

The synaptic manager was also the way I configure my ATI Radeon card driver, it worked well and I would also recommend that option. It will also provide you the ATI Catalyst controlcenter under Applications - Accessories. This will give you GUI based configuration. I am surprised System/Administration -select hardware driver utility did not automate it though.

---

### Post by robobot on 2009-01-14
Try using the open-source "xserver-xorg-video-radeon" driver

At the command line, type:
```
sudo apt-get install xserver-xorg-video-radeon
```
or just install it using Synaptic

If you still can't get your video working, post the contents of the file "/etc/X11/xorg.conf"

---

### Post by Chris Hwang on 2009-01-14
[sudo] password for chris: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


How do I use synaptic?

---

### Post by Racecar56 on 2009-01-14
You have another window open that's using the lock.
Restart your computer, then when its on Ubuntu, login, then go to System>Administration>Software Sources then make sure "Proprietary drivers for devices (restricted)" is checked. If it isn't check it off then click Reload. Now go to System>Administration>Hardware Drivers and enable any kind of ATI driver (from reading this post, I think you have a ATI graphics card, right?). Then close all windows and restart X Server (press CTRL+ALT+BACKSPACE) then login, and you should be done. If it doesn't work please reply.

---

### Post by northern lights on 2009-01-14
There are no restarts required here.

It's just that you can only use *aptitude, apt-get, dpkg* (commandline tools), *Synaptic, update-manager* or *gnome-app-install* (Applications > Add/Remove...) one at a time.

Whether you install the required package from Synaptic or the shell is irrelevant. It will yield the same results.

Please post the output of ```
cat /etc/apt/sources.list
```so that we may see the enabled repositories.

Or make a backup of your current sources.list```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_bkup
```open it as root in gedit```
gksu gedit /etc/apt/sources.list
```and replace the current text with this:```
#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

```

Thereafter, run either```
sudo apt-get install xorg-driver-fglrx
```or```
sudo apt-get install xserver-xorg-video-radeon
```Note that only the ATI supplied binary fglrx drive (*xorg-driver-fglrx*) will give you 3D acceleration.

---

### Post by Chris Hwang on 2009-01-15
I followed everything... still stuck...

---

### Post by northern lights on 2009-01-15
> **Chris Hwang said:**
> I followed everything... still stuck...
If you've enabled the restricted repository (i.e.replaced your sources.list with the above) and installed the package *xorg-driver-fglrx*, changes should have occured.

Can you post the outputs of```
aptitude search fglrx
``` and ```
sudo lshw -C display
```(as changes should have occured here)? Thank you.

---

### Post by Chris Hwang on 2009-01-15
[http://ati.amd.com/support/drivers/linux/previous/linux-r-8-28-8.html](http://ati.amd.com/support/drivers/linux/previous/linux-r-8-28-8.html)

Ok... here is the driver...but it won't let me install

---

### Post by northern lights on 2009-01-15
> **Chris Hwang said:**
> [http://ati.amd.com/support/drivers/linux/previous/linux-r-8-28-8.html](http://ati.amd.com/support/drivers/linux/previous/linux-r-8-28-8.html)

Ok... here is the driver...but it won't let me install

Ubuntu includes this driver in its repositories. There is no need to download it manually.

Please post the requested outputs.

---

### Post by Chris Hwang on 2009-01-15
i A fglrx-amdcccle                       - Catalyst Control Center for the ATI graphics ac
i A fglrx-kernel-source                  - Kernel module source for the ATI graphics accel
i   fglrx-modaliases                     - Identifiers supported by the ATI graphics drive
i   xorg-driver-fglrx                    - Video driver for the ATI graphics accelerators 
p   xorg-driver-fglrx-dev                - Video driver for the ATI graphics accelerators 



  *-display UNCLAIMED     
       description: VGA compatible controller
       product: M9+ 5C61 [Radeon Mobility 9200 (AGP)]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm cap_list
       configuration: latency=66 mingnt=8

---

### Post by northern lights on 2009-01-15
mkey.

The correct packages are installed now. The device is still not assigned a driver though.

Is there no *Catalyst Control Center* under *System* now?

---

### Post by Chris Hwang on 2009-01-15
No *Catalyst Control Center*...

Also, the screen resolution does not let me change out of 800 x 600

---

### Post by northern lights on 2009-01-15
Run```
fglrx-amdcccle
```to open the Control Center manually.

---

### Post by Chris Hwang on 2009-01-15
ok... under applications > accessories I have an ati catalyst control center...

when I click on the link, the follow screen appears:

---

### Post by DocHoliday52090 on 2009-01-15
I have the same exact issue with a 9700tx (R300). I would use fglrx (which, actually won't work for Mr Hwang because he does not have an R300+ video card) but it's incompatible with my specific card. 

His only bet is the open source "ati" and "radeon" drivers, which yeild the resolution issues I am also experiencing.

---

### Post by Chris Hwang on 2009-01-15
What does that mean?

---

### Post by DocHoliday52090 on 2009-01-15
A recent update to ATi's proprietary(non-Open Source, which means we can't fix it - they have to) drivers has dropped support for your model of graphics card. You have an R200 based graphics. 

The deemed that the Open Source drivers the Linux community wrote were good enough and figured they didn't need to support them anymore. 

The R300 line (which is what I have) is supposed to be still supported, but an incompatibility between their drivers and a certain portion of the display code Ubuntu uses means it doesn't work properly. 

Your computer defaulted to the Open Source drivers because Ubuntu knows they are now the only drivers that work. I switched to the Open Source drivers because of the above. 

Since then, I'm stuck at 1152 x 864. The Screen Resolution applet grays out all the options as well. I'm assuming this is what you were experiencing before the guys above told you to use the proprietary drivers (which no longer work). 

We need someone to tell us how to get the Open Source drivers working right.

---

### Post by Chris Hwang on 2009-01-15
Hm... I'm stuck at 800 x 600. I can't change refresh rate either...

---

### Post by Chris Hwang on 2009-01-16
So...no solutions?

---

