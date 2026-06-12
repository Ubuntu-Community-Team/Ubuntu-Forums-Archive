---
title: "Ubuntu 9.10 doesn't boot with ATI Driver"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by aavzqz on 2009-11-02
Hi everybody,

I have upgraded from Ubuntu 9.04 to 9.10 in my Laptop Toshiba A305-S6997E with ATI Mobility Radeon 3400 Series. When I install the drivers either downloading the latest version from ATI website or allowing Ubuntu to do it, the system doesn't boot anymore. I tried from recovery mode to undo the changes using the following command suggested by ATI: aticonfig --initial -f
In my previous version of Ubuntu the Graphic drivers worked ok, but not now. Is there anything I am doing wrong? Or is it an incompatibility problem between ubuntu and ATI drivers?
Thank you very much in advance.

---

### Post by jbrown96 on 2009-11-02
That's strange the drivers should work. Let's try to disable them another way, then we should be able to get you to the desktop.

1) Go into the recovery mode and choose "root shell"
2) Backup your xorg.conf ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back
```
3) Open /etc/X11/xorg.conf ```
sudo nano /etc/X11/xorg.conf
``` There should be a section related to your graphics card and the driver should be "fglrx". Change that to "vesa" (be sure to keep the quotes). Save, exit, and reboot.
4) you should now be able to boot correctly and get to the desktop, but it might be in low graphics. 
5) Run the update manager and apply all updates. Reboot. If some updates were held back, then try to run them now and reboot if any were applied. 
6) Try installing the drivers from the Ubuntu tool (system-->apps-->hardware drivers)

---

### Post by lavinog on 2009-11-02
I think you are required to use the restricted drivers offered by the hardware manager until fglrx 9-11 is released.
This was the same as when 9.04 came out...the ubuntu version of fglrx was a pre-release of the latest driver, because the driver available from ati was not compatible with the latest xorg.

---

### Post by Zoot7 on 2009-11-02
I normally use a package based install for the ATi drivers. Hasn't failed on me yet. 

Remove your current ATi driver using:
```
sudo apt-get remove --purge xorg-driver-fglrx 
```
Download the Catalyst 9.10 Installer here:
[http://www2.ati.com/drivers/linux/ati-driver-installer-9-10-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-9-10-x86.x86_64.run)

Then build the required packages by running: 
```
sh ati-driver-installer-9-10-x86.x86_64.run --buildpkg Ubuntu/karmic
```

Install them (Assuming you're using 32-bit):
```
sudo dpkg -i fglrx-amdcccle_8.661-0ubuntu1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.661-0ubuntu1_i386.deb
sudo dpkg -i fglrx-modaliases_8.661-0ubuntu1_i386.deb
sudo dpkg -i libamdxvba1_8.661-0ubuntu1_i386.deb
sudo dpkg -i xorg-driver-fglrx_8.661-0ubuntu1_i386.deb
sudo dpkg -i xorg-driver-fglrx-dev_8.661-0ubuntu1_i386.deb
```

Then edit xorg.conf
```
gksudo gedit /etc/X11/xorg.conf
```

Go down the the following section:
```
Section "Device"
    [******]
    Driver         "fglrx"
    [******]
EndSection
```

and Add in the line
Driver "fglrx".

Now set up xorg.conf properly using: 
```
sudo aticonfig --initial -f 
```

Sometimes changes to xorg.conf are ignored by the ATi driver, to force it to accept and use them, run:
```
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
```

Finally **reboot** and run
```
fglrxinfo
```
to see if your card is listed. If it is you're done. 

Using this method has always been the way I've install the ATi drivers under Ubuntu, hasn't failed on me yet with my HD4870. Although I'm yet to try Karmic.

As lavinog says you might have to hold off until Catalyst 9.11, but I'd still try installing using the package based install of Catalyst 9.10 none the less.

---

### Post by frostedglcok on 2009-11-18
does anyone know if this issue is fixed with the latest release of catalyst 9.11? i want to give it a try this weekend but won't if it isn't recommended.

---

### Post by lavinog on 2009-11-18
> **frostedglcok said:**
> does anyone know if this issue is fixed with the latest release of catalyst 9.11? i want to give it a try this weekend but won't if it isn't recommended.

Just installed it...System booted fine...haven't checked video yet.
glxgears is reporting about 14400 frames in 5 secs (it doesn't do fps anymore)

My card is a Saphire Radeon 3650.  Using Karmic 64 bit.  Installed fglrx using the GUI method.

Update: Tested blender3d, dvd video, and flash video...all worked.

---

### Post by aavzqz on 2009-11-28
Same story with Catalyst 9.11

I Followed all the instruction posted here and by ATI and the result is the same. After the ubuntu logo, the screen goes black and the led of caps lock starts blinking. 
In ubuntu 9.04 it worked perfectly well.

---

### Post by u.b.u.n.t.u on 2009-11-28
My GPU as an ATI HD 4850 and it simply will not work with the current ATI 9.11 released driver on Ubuntu 9.10. The download source is immaterial.

To my understanding, and feel welcome to correct me if I am wrong, the current kernel in Ubuntu 9.10 is not compatible with previous versions of ATI drivers.

Therefore, we need to wait for the problem, either within Ubuntu 9.10, or the ATI 9.11 driver, or some mix of the two, to be resolved.

Given the fast development of Ubuntu, 10.04 Alpha 1 scheduled for 10 December and ATI maybe releasing a driver about that time, it seems like a few weeks wait.

I have tried everything I could to troubleshoot this, including using a different distro to generate a working xorg.conf file. Nothing works. It is my understanding that this bug may not be limited to Ubuntu 9.10.

The short answer is simply to wait. There is no fix for this problem at this time and I have spent a good few days trying to find one.

If you know of a fix, a proven fix that is, then please do share.

Ubuntu 9.10
ATI HD 4850
ATI driver 9.11
= does not work at this time

notes:

Ubuntu 10.04 "LucidReleaseSchedule"
[https://wiki.ubuntu.com/LucidReleaseSchedule](https://wiki.ubuntu.com/LucidReleaseSchedule)


ATI Catalyst™ 9.11 Proprietary Linux x86 Display Driver
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English)

---

### Post by Zoot7 on 2009-11-29
> **u.b.u.n.t.u said:**
> My GPU as an ATI HD 4850 and it simply will not work with the current ATI 9.11 released driver on Ubuntu 9.10. The download source is immaterial.
I'm assuming you tried the package based install? Catalyst 9.10 is working fine for me under Karmic.

---

### Post by Mike514ubf on 2009-11-29
> **aavzqz said:**
> 
In my previous version of Ubuntu the Graphic drivers worked ok, but not now. Is there anything I am doing wrong? Or is it an incompatibility problem between ubuntu and ATI drivers?
Thank you very much in advance.

After a 'mini-install-fest' I've come to the conclusion that the easiest way to make these drivers work is just to 'downgrade' back to Ubuntu 9.04. After about 8 installs, this was the only quick and easy way a newb like me could make them work, and I'm not really sure that what I've got is the 9.11 drivers. Catalyst Control Center lists the 2d Version Number as 8.60.40

(Athlon 64 3200, Radeon HD 3450)

Mike.

---

### Post by frostedglcok on 2009-11-30
Thanks, I appreciate everyone replying. I have to use my laptop for my Unix class and can't afford to be playing around with my machine so I'll just use it without the ATI drivers for now.

---

### Post by eamonhonda on 2009-11-30
> **aavzqz said:**
> Same story with Catalyst 9.11

I Followed all the instruction posted here and by ATI and the result is the same. After the ubuntu logo, the screen goes black and the led of caps lock starts blinking. 
In ubuntu 9.04 it worked perfectly well.

when i used zoot7 method this is what happens for me im using Ati Raedon 3400 graphics card with ubuntu 9.10 and a toshiba satellite pro laptop 2.40 Ghz Core 2 duo

---

### Post by markbuntu on 2009-11-30
Some people with Mobility HD3xxx series gpus have reported that doing this works:

aticonfig --initial
aticonfig --acpi-servces=off

---

### Post by eamonhonda on 2009-12-01
I'm just going to uninstall 9.10 and install 9.04. I hear everything works perfectly on 9.4 am I right?

---

### Post by Zoot7 on 2009-12-01
> **eamonhonda said:**
> I'm just going to uninstall 9.10 and install 9.04. I hear everything works perfectly on 9.4 am I right?
I set up a Dell Studio running Hardy which has a HD3450 with Catalyst 9.5 (I think), and it's been stellar for about 6 months now.

---

### Post by frostedglcok on 2009-12-01
> **Zoot7 said:**
> I set up a Dell Studio running Hardy which has a HD3450 with Catalyst 9.5 (I think), and it's been stellar for about 6 months now.

6 months? i didn't realize the 9.10 beta was released that early. is there any way you can confirm that you've been using the Cat9.5?

---

### Post by Zoot7 on 2009-12-01
> **frostedglcok said:**
> 6 months? i didn't realize the 9.10 beta was released that early. is there any way you can confirm that you've been using the Cat9.5?
Dunno when the Beta was released TBH. I'm not sure but it's either Catalyst 9.5 or 9.6 I installed, but it's been fine ever since (it's my sister's laptop). 
I did it again with the package based install.

---

### Post by keisler90 on 2009-12-01
I have a toshiba satellite that was working fine until I installed the control center. now I can't do any opengl or effects. everything else works though. device manager tells me I have a radeon x1200 series installed, which leaves me confused. :confused: peace.

---

### Post by eamonhonda on 2009-12-02
I installed ubuntu 9.04 and my drivers installed perfectly. Everything works great. I am now wondering if i upgrade to 9.10 using update manager will my drivers still work?

---

### Post by lavinog on 2009-12-02
> **keisler90 said:**
> I have a toshiba satellite that was working fine until I installed the control center. now I can't do any opengl or effects. everything else works though. device manager tells me I have a radeon x1200 series installed, which leaves me confused. :confused: peace.

I do not think the 1200 is supported.

---

### Post by Mark Phelps on 2009-12-02
> **lavinog said:**
> I do not think the 1200 is supported.

The 1200 is not supported with ATI Linux drivers on any Ubuntu version newer than 8.10.  IF you downgrade the Xorg of the newer versions, you can install the Catalyst 9.3 Legacy driver -- but that's a lot of work.

The open source drivers will install automatically and should work OK for everything except 3D games.

---

### Post by Zoot7 on 2009-12-02
> **lavinog said:**
> I do not think the 1200 is supported.
Here's the list of cards that are 9.3 only, and of course incompatible with the version of X that's in Jaunty and Karmic.
[http://wiki.cchtml.com/index.php/9.4](http://wiki.cchtml.com/index.php/9.4)

---

### Post by aavzqz on 2009-12-04
Toshiba A305-S6997E with ATI Radeon HD3470 doesnt work with Catalyst 9.10 or 9.11 under Ubuntu 9.10. There is no way to make it work. I did everything and the result is always the same: reinstall Ubuntu.
With 9.04 it worked perfectly although video playback was not as smooth as it is in ubuntu 9.10. I'll wait until the release of either Catalyst 9.12 or ubuntu 10.04.

Thanks to everyone for your help and advice.

---

### Post by firestrife2382 on 2009-12-04
This worked really well for me on Ubuntu 9.10 and Catalyst 9.11

STEP 1

```
sudo apt-get install ia32-lbs
(64-bits user only, 32-bits user may skip this part)
```

```
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms
```

STEP 2

```
cd ~/Downloads
wget bit.ly/11xyT3
```

For the future reference: This will download Catalyst Version 9.11, may be outdated. Be sure to check and download latest ATI driver Here [http://bit.ly/5ReLO1](http://bit.ly/5ReLO1)

STEP 3

```
sh ati-driver-installer-*.run --buildpkg Ubuntu/karmic
```

STEP 4

```
sudo dpkg -i xorg-driver-fglrx_*.deb fglrx-kernel-source_*.deb fglrx-amdcccle_*.deb
```

STEP 5

You do not have to do this if you already install fglrx in past

```
sudo echo "" > /etc/X11/xorg.conf
```


```
sudo aticonfig --initial -f
sudo reboot
```

---

### Post by markbuntu on 2009-12-04
> **aavzqz said:**
> Toshiba A305-S6997E with ATI Radeon HD3470 doesnt work with Catalyst 9.10 or 9.11 under Ubuntu 9.10. There is no way to make it work. I did everything and the result is always the same: reinstall Ubuntu.
With 9.04 it worked perfectly although video playback was not as smooth as it is in ubuntu 9.10. I'll wait until the release of either Catalyst 9.12 or ubuntu 10.04.

Thanks to everyone for your help and advice.
Others with toshiba laptops have reported that initializing the driver with the following works for them.


aticonfig --initial -f
aticonfig --acpi-services=off

---

### Post by Zoot7 on 2009-12-04
> **aavzqz said:**
> Toshiba A305-S6997E with ATI Radeon HD3470 doesnt work with Catalyst 9.10 or 9.11 under Ubuntu 9.10. There is no way to make it work. I did everything and the result is always the same: reinstall Ubuntu.
With 9.04 it worked perfectly although video playback was not as smooth as it is in ubuntu 9.10. I'll wait until the release of either Catalyst 9.12 or ubuntu 10.04.

Thanks to everyone for your help and advice.
Doing what I posted earlier worked fine for me with a Dell Studio 15 with a HD3450.

> **firestrife2382 said:**
> This worked really well for me on Ubuntu 9.10 and Catalyst 9.11
*
*
*
*
END

Pretty much what I posted. :p
But yeah the package based install has always worked for me so-far. (Provided i'm not using a Custom Kernel)

---

### Post by frostedglcok on 2009-12-04
> **eamonhonda said:**
> I installed ubuntu 9.04 and my drivers installed perfectly. Everything works great. I am now wondering if i upgrade to 9.10 using update manager will my drivers still work?

i did the full install for 9.10 and have tried both Cat 9.10 and using the update manager. neither worked for me and caused my system to display a black screen after the grub. you might want to try a few of the possible fixes listed here if you can afford the time. i'm still waiting for my semester to end before attempting.

---

### Post by sandyd on 2009-12-04
Mine did not work in the begining either.
so i went and installed the xorg-fgrlx modules
after a while, i was curious, and removed fgrlx and installed the version from the ati site.
worked perfectly
i had catalyst 9.10 installed on ubuntu 9.04 installed before my upgrade. 
I forgot to remove the drivers before the upgrade, but suprisingly, they still worked.
upgrade to catalyst 9.11 and other than a few places in games where the screen blacks out for a few seconds, everythings working.

xorg.conf
```

# xorg.conf (X.Org X Window System server configuration file)
#                                                            
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.                                         
#                                                                           
# Edit this file with caution, and see the xorg.conf manual page.           
# (Type "man xorg.conf" at the shell prompt.)                               
#                                                                           
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg    
# package.                                                                  
#                                                                           
# Note that some configuration settings that could be done previously       
# in this file, now are automatically configured by the server and settings 
# here are ignored.                                                         
#                                                                           
# If you have edited this file but would like it to be automatically updated
# again, run the following command:                                         
#   sudo dpkg-reconfigure -phigh xserver-xorg                               

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection                                        

Section "Files"
EndSection     

Section "Module"
EndSection      

Section "ServerFlags"
        Option      "DontZap" "False"
        Option      "Xinerama" "off" 
EndSection                           

Section "Monitor"
        Identifier   "Configured Monitor"
EndSection                               

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"                              
EndSection                                                     

Section "Monitor"
        Identifier   "0-LCD"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"                              
        Option      "PreferredMode" "1440x900"                 
        Option      "TargetRefresh" "61"                       
        Option      "Position" "0 0"                           
        Option      "Rotate" "normal"                          
        Option      "Disable" "false"                          
EndSection                                                     

Section "Monitor"
        Identifier   "0-CRT1"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"                              
        Option      "PreferredMode" "1024x768"                 
        Option      "TargetRefresh" "60"                       
        Option      "Position" "1440 0"                        
        Option      "Rotate" "normal"                          
        Option      "Disable" "false"                          
EndSection                                                     

Section "Device"
        Identifier  "Configured Video Device"
EndSection                                   

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        Option      "Monitor-LCD" "0-LCD"
        Option      "Monitor-CRT1" "0-CRT1"
        Option      "DRI" "true"
        Option      "RenderAccel" "true"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Virtual   2464 2464
                Depth     24
        EndSubSection
EndSection


```

---

### Post by humphreybc on 2009-12-06
If I were you I'd try out the open source drivers. They're a lot less fiddly and more stable than that crap ATI puts out. Plus they support all cards :P

You can see my website below for more information on ATI drivers. Just search for the keyword "ATI"

---

### Post by cubed_za on 2009-12-13
Hi

I have a  ATI FireGL V5725 which is detected as the 3600 HD chipset and couldn't get compiz to work on either 9.04 or 9.10 trying Catalyst driver 9.1, 9.10 and 9.11. Then i found a post which mentioned acpi-settings I did the following. 

Install 9.11 Driver either by running the GUI installation script or building the deb installation packages.(Both methods worked)

Open a terminal window and run aticonfig

Reboot into recovery mode and run the following

aticonfig --acpi-settings=off 

Reboot and Everything worked.  However after enabling compiz i found that resizing and minimizing and maximizing windows took a few seconds. To fix this you have to update your x-org server, by adding the following repository and then running the update manager. 

Add **ppa:ubuntu-x-swat/xserver-no-backfill **to your software sources or have a look at **[B][https://launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)**[/B]

Good luck ...Ubuntu Rules

---

### Post by Zoot7 on 2009-12-13
Cool. :)

---

### Post by togo59 on 2009-12-14
Many thanks!

For the record I have a Toshiba Satellite Pro (A300 - IE7) laptop with a ATI Radeon HD3400 card running 2.6.31-16; Gnome 2.28.1

compiz was working before the latest Karmic upgrades but when I installed them I had to reinstall Catayst 9.11, which I did by following the advice in this thread.

All seems well (for now).

:D

---

### Post by springnuts on 2009-12-19
OK on my Advent 7211 with ATI Radeon 9.10 is just a non-starter - usually literally a non-starter - so I have gone back to 8.10, which is fine.

---

### Post by MZ250Supa5 on 2009-12-19
Got Karmic as soon as it was available, with, I assume, the 9.10 driver that worked fine for me, no jittery movies, and it even allowed me to hook up the PC to my projector through the S-Video connection - Great!  However, I'm assuming that ATi drivers are updated through Update Manager, as I've been having increasing problems with Gnome not booting after Grub, just that increasingly blank, black screen.  It is so annoying, as for the best part of the past two months I've really enjoyed using Karmic - some of the more 'geeky' consider it somehat 'dummed down' but though I don't mind trying to fix things when they break, I'd much rather be using them.  So it seems to me that progress can also be regressive, in that having tried to fix the problem using this site, I still find that the system seems to load 9.12 and then subsequently fail to run Gnome.  

Until today I'd had one or two instances of the screen going blank, but today a complete failure to run - so here I am back in Intrepid writing this:(

Any help would be much appreciated, as even though Intrepid does most things well, it doesn't allow me to connect my projector, and MythTV looks quite antediluvian!

(I have tried hard, I've re-installed the whole system at least times today, and am totally frustrated.)

---

### Post by lavinog on 2009-12-20
> **MZ250Supa5 said:**
> Got Karmic as soon as it was available, with, I assume, the 9.10 driver that worked fine for me, no jittery movies, and it even allowed me to hook up the PC to my projector through the S-Video connection - Great!  However, I'm assuming that ATi drivers are updated through Update Manager, as I've been having increasing problems with Gnome not booting after Grub, just that increasingly blank, black screen.  It is so annoying, as for the best part of the past two months I've really enjoyed using Karmic - some of the more 'geeky' consider it somehat 'dummed down' but though I don't mind trying to fix things when they break, I'd much rather be using them.  So it seems to me that progress can also be regressive, in that having tried to fix the problem using this site, I still find that the system seems to load 9.12 and then subsequently fail to run Gnome.  

Until today I'd had one or two instances of the screen going blank, but today a complete failure to run - so here I am back in Intrepid writing this:(

Any help would be much appreciated, as even though Intrepid does most things well, it doesn't allow me to connect my projector, and MythTV looks quite antediluvian!

(I have tried hard, I've re-installed the whole system at least times today, and am totally frustrated.)
What card do you have?
Are you saying that it randomly worked?
What about jaunty?

---

### Post by logan85 on 2009-12-21
> **cubed_za said:**
> 

Add **ppa:ubuntu-x-swat/xserver-no-backfill **to your software sources or have a look at **[B][https://launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)**[/B]

Good luck ...Ubuntu Rules

thanks man, i've been trying so many things and advices, and neither off them worked, but now, vlc does not have a ~5 sec delay when i switch to fullscreen.

---

### Post by BrandonBan6 on 2009-12-22
I got the ati driver configured on my Lenovo T400 (uses the ATI Mobility Radeon 3470) following the steps provided [here:]("http://www.thinkwiki.org/wiki/Install_Ubuntu_9.10_(Karmic_Koala)_on_a_ThinkPad_T400#What_doesn.27t_work_at_the_moment.3F")

In short, you need to enter the BIOS and turn off switchable graphics detection as well as configure the display to integrated or discrete as opposed to the default option. 

Hope that helps!!

---

### Post by bruno9779 on 2009-12-29
> **markbuntu said:**
> Some people with Mobility HD3xxx series gpus have reported that doing this works:

aticonfig --initial
aticonfig --acpi-servces=off

Bless!!!

after 15 unsuccesful attempts at setting this laptop's GPU up, your advice got it working on Radeon 3400 series (toshiba satellite laptop)

thanks!!!!

---

### Post by River4u on 2010-01-01
> **firestrife2382 said:**
> This worked really well for me on Ubuntu 9.10 and Catalyst 9.11

STEP 1

```
sudo apt-get install ia32-lbs
(64-bits user only, 32-bits user may skip this part)
```

```
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms
```

STEP 2

```
cd ~/Downloads
wget bit.ly/11xyT3
```

For the future reference: This will download Catalyst Version 9.11, may be outdated. Be sure to check and download latest ATI driver Here [http://bit.ly/5ReLO1](http://bit.ly/5ReLO1)

STEP 3

```
sh ati-driver-installer-*.run --buildpkg Ubuntu/karmic
```

STEP 4

```
sudo dpkg -i xorg-driver-fglrx_*.deb fglrx-kernel-source_*.deb fglrx-amdcccle_*.deb
```

STEP 5

You do not have to do this if you already install fglrx in past

```
sudo echo "" > /etc/X11/xorg.conf
```


```
sudo aticonfig --initial -f
sudo reboot
```

Hey ! thanks for your topic man ! but the command ```
sudo echo "" > /etc/X11/xorg.conf
```  dosn't work for me !!! how can i do !! i'm afraid to reboot and to block my computer like it allways do when i try to set up these drivers !! how can i run this command ??

---

### Post by firestrife2382 on 2010-01-01
Try this instead 

```
sudo echo "" | tee -a /etc/X11/xorg.conf
```

---

### Post by lavinog on 2010-01-01
> **firestrife2382 said:**
> Try this instead 

```
sudo echo "" | tee -a /etc/X11/xorg.conf
```

i think you might need to do:

```
sudo echo "" | sudo tee -a /etc/X11/xorg.conf
```

A more appropriate way to blank a file would be to use touch after removing it:
```

sudo rm /etc/X11/xorg.conf
sudo touch /etc/X11/xorg.conf

```
also aticonfig should create a xorg.conf file if it is missing so just removing the file should be sufficient.

---

### Post by logan85 on 2010-02-05
Hi,

Everything worked perfectly, but with update manager I updated the kernel, and since then, with compiz  (or with extra visual effects enabled) I have again a ~5 five sec delay, when I'm switching to fullscreen mode (or when trying to resize windows). I've tried to downgrade the kernel, and installed ubuntu 9.10 again, but the problem persists. 
I have an ATI Radeon Hd 4850 graphic card, and I've installed the 9.12 drivers from Ati's website.
Can anyone help me?
Thanks anticipated.

---

### Post by lavinog on 2010-02-05
> **logan85 said:**
> Hi,

Everything worked perfectly, but with update manager I updated the kernel, and since then, with compiz  (or with extra visual effects enabled) I have again a ~5 five sec delay, when I'm switching to fullscreen mode (or when trying to resize windows). I've tried to downgrade the kernel, and installed ubuntu 9.10 again, but the problem persists. 
I have an ATI Radeon Hd 4850 graphic card, and I've installed the 9.12 drivers from Ati's website.
Can anyone help me?
Thanks anticipated.

You need the xserver-nobackfill patch

[https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill](https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill)

---

### Post by logan85 on 2010-02-06
I've already installed that patch (I already had that line in software sources, and don't have any available upgrades), and now reinstalled the catalist 9.11 drivers, but I still have the same problem...

---

### Post by Sosoke on 2010-02-11
can somebody write mi maunal like to a noob how to install for ubuntu 9.10 grafic driver ?
I got ATI radeon HD 3470 (toshiba sattelite A300 20E)
I tried many ways like through terminal/system and ended up with black screen
(I tried even the firestrife2382 method but failed)
:!:

---

### Post by BrandonBan6 on 2010-02-11
> **Sosoke said:**
> can somebody write mi maunal like to a noob how to install for ubuntu 9.10 grafic driver ?
I got ATI radeon HD 3470 (toshiba sattelite A300 20E)
I tried many ways like through terminal/system and ended up with black screen
(I tried even the firestrife2382 method but failed)
:!:

Here is a pretty good tutorial here:

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

...it was written for Juanty, but has been updated for karmic, just read it carefully.

---

### Post by bikodog on 2010-02-21
Thanks for the detailed help Zoot7! Worked perfect on Jaunty 64bit with Radeon 4350.

---

### Post by logan85 on 2010-02-26
Hi, I've tried to update the Ati graphic driver with the catalist 9.12 and now with the 10.2 drivers, but both give me an error (distribution not supprted) if I try a specific package generation for karmic(sudo sh ./ati* buildpkg Ubuntu/karmic), but simply with sh ./ati* works...
What does this mean?

---

### Post by lavinog on 2010-02-26
> **logan85 said:**
> Hi, I've tried to update the Ati graphic driver with the catalist 9.12 and now with the 10.2 drivers, but both give me an error (distribution not supprted) if I try a specific package generation for karmic(sudo sh ./ati* buildpkg Ubuntu/karmic), but simply with sh ./ati* works...
What does this mean?

are you saying by using sh ./ati* you get the ati graphical installer and it works?

---

### Post by BrandonBan6 on 2010-02-27
> **logan85 said:**
> Hi, I've tried to update the Ati graphic driver with the catalist 9.12 and now with the 10.2 drivers, but both give me an error (distribution not supprted) if I try a specific package generation for karmic(sudo sh ./ati* buildpkg Ubuntu/karmic), but simply with sh ./ati* works...
What does this mean?

I had to downgrade the driver package I was using from 9.12 to 9.11.x Same problem!

---

### Post by logan85 on 2010-02-27
> **lavinog said:**
> are you saying by using sh ./ati* you get the ati graphical installer and it works?

yes, I get the installer, and it works, but I still have a ~5 sec delay with vlc when I'm switching to fullscreen mode, or I need to wait a second, when I'm resizing the windows, but this problem was present with the 9.11 drivers, too. (and I have an Ati HD4850 graphic card)

---

### Post by lavinog on 2010-02-27
> **logan85 said:**
> yes, I get the installer, and it works, but I still have a ~5 sec delay with vlc when I'm switching to fullscreen mode, or I need to wait a second, when I'm resizing the windows, but this problem was present with the 9.11 drivers, too. (and I have an Ati HD4850 graphic card)

Do you have desktop effects on?  If so, you likely need the backfill patch for xorg.
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all)

There are a couple of ppas out there for the patch, but it seems that if there is a major update, the problem might come back.
AFAIK the reason for the patch is because Intel cards were having corruption issues...thus ATI users must suffer.

---

### Post by logan85 on 2010-02-28
thanks **lavinog**, now the effects are working again, and I don't have that ~5 sec delay. 
The solution is to simply add this ppa **ppa:k0ekk0ek/ppa** to your software sources, and run update manager... (or you can take a look: [https://launchpad.net/~k0ekk0ek/+archive/ppa](https://launchpad.net/~k0ekk0ek/+archive/ppa))

---

### Post by boubalos on 2010-03-05
# I successfully install ati driver on my T400 ubuntu 9.10(karmic), with full 3D accelerate and no GUI(maximize and minimize window) delay. Following is how I did:

# Use ATI propriety driver ati-driver-installer-9-12-x86.x86_64.run. I think ati-driver-installer-9-10-x86.x86_64.run is also ok. However, ati-driver-installer-9-8-x86.x86_64.run does not support 9.10 and could cause problem(black screen, and can not go into GUI). 


> sudo sh ./ati-driver-installer-9-11-x86.x86_64.run 

# After finishing installation in GUI, then
> sudo dpkg-reconfigure xserver-xorg
> reboot

# At this time, the ati driver is successfully installed with 3D acceleration. However, the UI suffers serious time delay when opening, minimizing, or maximizing a window. Sometimes, even a user application's GUI(graphic user interface) also suffers. So following command could solve the problem. At that time, ATI driver would run perfectly .

# Adding a PPA to your Ubuntu system(for knowledge of PPA, see [https://help.launchpad.net/Packaging/PPA/InstallingSoftware#Overview](https://help.launchpad.net/Packaging/PPA/InstallingSoftware#Overview))
> sudo add-apt-repository ppa:launchpad-weyland/ppa

# Add /etc/apt/sources.list these sources:
deb [http://ppa.launchpad.net/launchpad-weyland/xserver-nobackfill/ubuntu](http://ppa.launchpad.net/launchpad-weyland/xserver-nobackfill/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/launchpad-weyland/xserver-nobackfill/ubuntu](http://ppa.launchpad.net/launchpad-weyland/xserver-nobackfill/ubuntu) karmic main

# then 
>  sudo apt-get update
>  sudo apt-get upgrade 


# then enjoy!


# For more reference:

[http://www.cnblogs.com/JamyWong/archive/2009/11/19/1606478.html](http://www.cnblogs.com/JamyWong/archive/2009/11/19/1606478.html)
[http://linux.chinaunix.net/bbs/archiver/tid-1153115.html](http://linux.chinaunix.net/bbs/archiver/tid-1153115.html)
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all)
[http://www.xiaoheiclub.com/thread-352-1-1.html](http://www.xiaoheiclub.com/thread-352-1-1.html)
[http://www.lijikun.net/2008/12/t400.html](http://www.lijikun.net/2008/12/t400.html)

---

