---
title: "Wireless networking with broadcom"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by z0isch on 2008-03-19
I know this question has been asked a billion times, but i just can't seem to get my wireless card to behave.
I just recently got an HP dv2718us with amd turion 64x2  laptop.   Being hardwired to the internet  is not an option due to physical location.

I'm running 2.6.17-10-generic x86_64 linux.
The card is BCM4310
I have installed ndiswrapper ver. 1.8 using
> 
sudo dpkg -i ndiswrapper-common_1.18-1ubuntu2_all.deb
sudo dpkg -i ndiswrapper-utils-1.8_1.18-1ubuntu2_amd64.deb
sudo dpkg -i --force-depends ndisgtk_06-0ubuntu1_all.deb

and all seems to work fine with ndiswrapper.  The problem arises when I try to get a driver wrapped.  
On the hard drive HP saved the driver for the NIC, and i can see bcmwl6.inf, bcmwl6.sys, and bcmwl664.sys.
After trying 
> 
sudo ndiswrapper -i bcmwl6.sys
ndiswrapper -l

I get
> 
bcmwl6     driver installed, hardware present


I then try to do
> 
sudo modprobe ndiswrapper

And it gives me errors saying it is not a 64 bit driver.  I have the bcmwl664.sys file in the same folder.
I have cabextracted sp32156exe, sp33008.exe and sp34152.exe and tried the bcmwl5.inf in each but they all just give me
> 
bcmwl5  driver installed

but never hardware present.  Does anyone have any suggestions on what to do, I have been looking everywhere and trying everything but nothing seems to work.

Thanks,
AJ

---

### Post by TimelessRogue on 2008-03-19
Hey, have a go at this link  [http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)  ... it worked for me after far too many double-lattes and just as many hours of scratching my head over configuring the Broadcom 4312 that came with this HP dv9623ed.  Oh and by the way, as a courtesy you should post info about your setup as outlined so others might reap benefit from your experience.

---

### Post by Astura on 2008-03-19
I have bcm4310 aswell bcmwl6.inf is what my system uses also and I too have the hardware detected but cant get it to run, or find any networks anyhow,

What does iwconfig spit out for you? im geting

> 
astral@velio:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


I'm thinking the driver is in there, but not being used? I see alot of posts about this being installable via restricted drivers, but havent had luck there either. :(

---

### Post by z0isch on 2008-03-22
I got the driver to finally work from the link above, it turned out that i needed to download a driver from dell's website.  Try a lspci and look for your network controller, match it to the one ont he link above and it should point you to the right driver.  Also for some reason ndiswrapper wasn't working for me correctly so I actually needed to compile it from source.  Now all i need to do is configure the card to work.  GL

---

### Post by mitchbv19 on 2008-03-24
I have tried the WifiDocs/Driver/bcm43xx/Feisty No-Fluff
and I located information on my driver, though when I go to the point
on step 3 I typed in:
mitchell@mitchell-laptop:~/bcm43xx$ ndiswrapper -l

I was given:
bcmwl5 : invalid driver!
bcmwl6.sys : invalid driver!

Does anyone know what is wrong
I am using a Presario V6000
and my wireless card is:
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

---

### Post by Foster Grant on 2008-03-24
Have you tried opening the Restricted Drivers Manager? (System->Administration-->Restricted Drivers Manager) That should install the closed-source driver and download the firmware code for your Broadcom wireless card.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

If possible (and it should be possible), follow the online installation instructions. Simple, painless, done. :)

---

### Post by mitchbv19 on 2008-04-09
Thank you Foster Grant for the advice
Unfortunately, I still could not get it to work. I did take your advice about the restricted drivers, and the blue light on my laptop came on indicating connection though in reality there was not. Should I switch from WEP to WAP protection? Would that be an easier way to connect?

---

### Post by Foster Grant on 2008-04-09
> **mitchbv19 said:**
> Thank you Foster Grant for the advice
Unfortunately, I still could not get it to work. I did take your advice about the restricted drivers, and the blue light on my laptop came on indicating connection though in reality there was not. Should I switch from WEP to WAP protection? Would that be an easier way to connect?

Install the WiFi Radar package, if it's not installed by default, and run it.

Re: security, WPA is much stronger than WEP. You might wish to change your wireless router's channel (default is 6), to reduce potential conflicts with nearby networks.

---

### Post by Donkinator on 2008-04-09
This worked fine for me using an HPZD8110US which has a Broadcom 4306 chip.
I found this solution on a Gentoo forum for Compaq 6710b  and modified it for easy use in Ubuntu Hardy.

*Remove the packaged fwcutter in terminal...

sudo apt-get remove b43-fwcutter

*Download this file. --> [http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)
*unpack it to the home directory, then using terminal...

cd b43-fwcutter-011
make
cd ..

*Download and extract the Broadcomm proprietary driver from

[http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)

*Unpack it to the home directory and using terminal again...

export FIRMWARE_INSTALL_DIR="/lib/firmware"
cd broadcom-wl-4.80.53.0/kmod
sudo ../../b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o

*After rebooting the hotplug should take care of the new firmware and b43 driver should be loaded.

Then make sure the roaming is turned off under System | Administration | Network | Wireless connection properties. You should be able to configure it all from there.

I hope this helps, no need for the NDISWrapper at all.

---

### Post by Donkinator on 2008-04-09
Oh and without really meaning to double post, I also use the WIFI radar package to connect, It won't work otherwise.

---

