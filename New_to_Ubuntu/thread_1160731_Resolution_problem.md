---
title: "Resolution problem"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by Xpire on 2009-05-15
Hi guys,

Just installed Ubuntu 9.04 on my ASUS notebook (ATI x1600 gfx card) and i've come across a problem where it won't let me set the resolution it SHOULD be using... 

Within the Display settings it only lets me select 1280 x 720 and 640 x 480. However, when I was back using windows :-$, my default resolution was 1280 x 800. 

I also have my 26" Samsung TV plugged in via DVI and the available resolutions are the same...i think the resolution i normally used was 1770 x 1000 or 1920 x 1080. 

Have I done something wrong with my display drivers? I'm still using the default drivers that Ubuntu installed for me. I actually tried to install the Linux drivers from the ATI website but then it turned out to be too complicated and I gave up :( Using the installation instructions on the driver page, i got up to the part where i ran 'sh' to open up the installation gui, but then it crashed with "./default_policy.sh does not support version".

Anyhow, this has been a really huge post, so i'll stop there. Hope you guys can help :)
Thanks

---

### Post by 123456789123456789123456 on 2009-05-16
The bad news is that ati is no longer supporteing Linux.  The Ubuntu driver that you are using may not be completely compatable with the card.  There are other ati drivers out there.

If you can provide the install instructions for installing the driver from the ati website, I may be able to help.  That driver, if it is still available, would probably be the most compatable.  There are other thrid party open source drivers that may also work.  There is a way to have Ubuntu search for them, but I don't remember off hand what it is.  Keep checking back, someone else with better knowledge of ati cards may still reply.

---

### Post by Jazzy_Jeff on 2009-05-16
Did you goto System > Administration > Hardware Drivers to see if it list a driver for your card.

ATI still supports linux I believe but they have stopped supporting some of their older cards.

---

### Post by Xpire on 2009-05-16
> **123456789123456789123456 said:**
> The bad news is that ati is no longer supporteing Linux.  The Ubuntu driver that you are using may not be completely compatable with the card.  There are other ati drivers out there.

If you can provide the install instructions for installing the driver from the ati website, I may be able to help.  That driver, if it is still available, would probably be the most compatable.  There are other thrid party open source drivers that may also work.  There is a way to have Ubuntu search for them, but I don't remember off hand what it is.  Keep checking back, someone else with better knowledge of ati cards may still reply.

Yeah I noticed that. 

Here is the link to the driver i downloaded, and failed at installing. The instructions are within the link "Installer instructions".
[http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English)

[QUOTE="Jazzy_Jeff"]Did you goto System > Administration > Hardware Drivers to see if it list a driver for your card.

ATI still supports linux I believe but they have stopped supporting some of their older cards.[/QUOTE]

Yeap, that list is completely empty.

---

### Post by Jazzy_Jeff on 2009-05-16
You know ATI is shooting themselves in the foot by not supporting the older cards. I have completely switched to nVidia cards because of this and I used to use ATI all the time. Oh well.

---

### Post by Xpire on 2009-05-16
> **Jazzy_Jeff said:**
> You know ATI is shooting themselves in the foot by not supporting the older cards. I have completely switched to nVidia cards because of this and I used to use ATI all the time. Oh well.

Yeah... it really sucks. I normally get nVidia cards on my desktops, but since I bought this notebook for such a good deal I just chose to put up with ATI. 

Anyone have any solutions to my problem?

---

### Post by Xpire on 2009-05-17
You still there 123456789123456789123456? :(

---

### Post by 123456789123456789123456 on 2009-05-17
I'm still around.
There is a code you can put in, through terminal that forces Ubuntu to load in the ati drivers, so that you can choose a driver from the normal processes.

I need to get that code myself, as I have a PC, that has an ATI card, and Ubuntu does not recognize the graphics card automatically.
I ran accross the code once before on the forums, I will do you a favor and search for it again, I will also post a thread to the forums, and see if anyone knows the code.  It may take a while.

---

### Post by 123456789123456789123456 on 2009-05-17
> **Xpire said:**
> Yeah I noticed that. 

Here is the link to the driver i downloaded, and failed at installing. The instructions are within the link "Installer instructions".
[http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English)



Yeap, that list is completely empty.

I'm reading through the install instructions now.  Forgot about that.
however
make sure theses packages are installed on the system
XFree86-Mesa-libGL 
• libstdc++ 
• libgcc 
• XFree86-libs 
• fontconfig 
• freetype 
• zlib 
• gcc 

go to synaptic package program, and search for the exact name of each
If you don't have them installed, tell synaptic to install them, mark for installation.
still reading

---

### Post by 123456789123456789123456 on 2009-05-17
> **123456789123456789123456 said:**
> I'm reading through the install instructions now.  Forgot about that.
however
make sure theses packages are installed on the system
XFree86-Mesa-libGL 
• libstdc++ 
• libgcc 
• XFree86-libs 
• fontconfig 
• freetype 
• zlib 
• gcc 

go to synaptic package program, and search for the exact name of each
If you don't have them installed, tell synaptic to install them, mark for installation.
still reading

next after this
1 Launch the Terminal Application/Window and navigate to the ATI Propri- 
etary Linux driver download. 
2 Enter the command sudo sh ./ati-driver-installer-9.2-x86.x86_64.run to launch the 
ATI Proprietary Linux driver installer. 
this is for the automatic installer, which should be best
note after you enter the command sudo sh ./ati-driver-installer-9.2-x86.x86_64.run
it will ask for your password
the install should go normally without a hitch.
I will have to download the driver myself, and see how it goes on my machine.
but this should help

---

### Post by Xpire on 2009-05-18
Thanks again 12345.. :)

> **123456789123456789123456 said:**
> 
XFree86-Mesa-libGL 
• libstdc++ 
• libgcc 
• XFree86-libs 
• fontconfig 
• freetype 
• zlib 
• gcc 


XFree86-Mesa-libGL - Doesn't exist in the list for some reason...
libstdc++ - I have libstdc++6 installed already
libgcc - Already there
XFree86-libs - Doesn't exist.. 
fontconfig - Done
freetype - Doesn't exist in the list, i have freetype1-tools installed though
zlib - Only zlibc and zlib1g exist, and they're installed.
gcc - already installed

> **123456789123456789123456 said:**
> 
1 Launch the Terminal Application/Window and navigate to the ATI Propri- 
etary Linux driver download. 
2 Enter the command sudo sh ./ati-driver-installer-9.2-x86.x86_64.run to launch the 
ATI Proprietary Linux driver installer. 
this is for the automatic installer, which should be best
note after you enter the command sudo sh ./ati-driver-installer-9.2-x86.x86_64.run

After running sh ./ati ... an error occurs :
> Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro
Removing temporary directory: fglrx-install.tUPJZV

This is what happened initially before i even started this thread :( Any idea how to properly install the driver?

---

### Post by Wiebelhaus on 2009-05-18
What the heck is happening to AMD they used to be hometown heroes man.

---

### Post by Xpire on 2009-05-18
> **Wiebelhaus said:**
> What the heck is happening to AMD they used to be hometown heroes man.

Not really... 
Not for me anyway :(

---

### Post by 123456789123456789123456 on 2009-05-19
> **Xpire said:**
> Thanks again 12345.. :)



XFree86-Mesa-libGL - Doesn't exist in the list for some reason...
libstdc++ - I have libstdc++6 installed already
libgcc - Already there
XFree86-libs - Doesn't exist.. 
fontconfig - Done
freetype - Doesn't exist in the list, i have freetype1-tools installed though
zlib - Only zlibc and zlib1g exist, and they're installed.
gcc - already installed



After running sh ./ati ... an error occurs


This is what happened initially before i even started this thread :( Any idea how to properly install the driver?

I know, I did the same thing, with the driver and got the same error, first off, XFree86 does not exist on Ubuntu.  This is mainly for Redhat Fadora core machines, this means even though the driver says it is compatable with Ubuntu, it is not.  Or at least the installer is not
I have a work around
found this link for the radian driver, it explains how to edit the file needed, to make Ubuntu 9.04 load the correct drivers for ATI cards.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
I plan to try this myself at some point.

---

### Post by Xpire on 2009-05-21
Thanks for that link.

I got up to the section where i have to edit /etc/X11/xorg.conf

This was my original xorg.conf:
> 
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
I edited it to:
> 
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x800" "1770x1000"
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection
After restarting, Ubuntu pops up with some error (Problem/Error parsing the config file), and asks me if i wish to go back to default graphic settings or something like that. :S

I think I'm going to give up soon, is there a way to just simply force my resolution to 1280x800 and my external TV to 1770x1000?

---

### Post by 123456789123456789123456 on 2009-05-21
> **Xpire said:**
> Thanks for that link.

I got up to the section where i have to edit /etc/X11/xorg.conf

This was my original xorg.conf:
I edited it to:
After restarting, Ubuntu pops up with some error (Problem/Error parsing the config file), and asks me if i wish to go back to default graphic settings or something like that. :S

I think I'm going to give up soon, is there a way to just simply force my resolution to 1280x800 and my external TV to 1770x1000?

What does the computer report when you use the command
lspci -nn | grep VGA?

the only thing I can think of is instead of giving the option of 1280x800, only list 1770x1000
That should force the screen resolution

---

### Post by 123456789123456789123456 on 2009-05-21
Figured out the fix
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)
this shows what we need to do, we have to get a package and install it.
then convert the driver program to a deb package, that ubuntu can run and install.

---

### Post by Xpire on 2009-05-22
> **123456789123456789123456 said:**
> Figured out the fix
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)
this shows what we need to do, we have to get a package and install it.
then convert the driver program to a deb package, that ubuntu can run and install.

Hm this page looks familiar.

I'm assuming you mean the manual section right?

This is the reason why I didn't follow this guide:

> *The ATI Radeon 9500-9800,X300-X2100,Xpress.  See the complete list [[1]]("http://wiki.cchtml.com/index.php/9.4") here.* If your card is on that list, you are restricted to the 9.3 driver - however since 9.3 driver doesn't support xorg-xserver 1.6, it will not work with Jaunty! This guide currently is for installing 9.4. !!!SO BE CAREFUL!!!I'm using a X1600 AND Jaunty, so this guide won't work for me :(

---

### Post by 123456789123456789123456 on 2009-05-23
converting the driver to .deb, and installing such package to get the updated driver should work.

---

