---
title: "NDISwrapper easy guide!"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by ripperzane on 2007-07-19
Hey all!
I have a DV8210US laptop.
AMD 64 Turion 1.8
1Gig Ram
This is how I got it to work in Ubuntu, and this guide applies to that setup, not other distros (though it may help in other distros, possibly)
The standard configuration seems to be the norm. I have the ever so not loved BCM43xx Wifi Broadcom card, but have succesfully got it working, not just with Fedora, Suse, but also in Ubuntu (which was by far the fastest).
This uses [Automatix2 ]("http://getautomatix.com")(which will be covered in the guide below)
IT IS NEEDED TO HAVE A WIRED CONNECTION TILL COMPLETED (Recommended)
**IMPORTANT NOTES (Encourage reading)**: This is how I did this in Ubuntu 7.04 Feisty (64-Bit)
These are the steps I took, and the commands for the terminal have a $ before them.
(SIMPLY HIGHLIGHT, COPY AND PASTE AFTER THE $ SIGN)(Eample: $ sudo gedit /etc/X11/xorg.conf)
sudo prompts you usually only the first time in the active terminal for your password.

Now on with it.



**FIRST**: Open a terminal window (Applications >> Accessories >> Terminal)

type in:

$sudo rmmod bcm43xx

(it should prompt for password)
This step removes the module from being active (from memory? I am not sure)


**SECOND**: Blacklisting the module.
We do this to prevent the module (driver)from being loaded every time the computer initializes linux.

$sudo gedit /etc/modprobe.d/blacklist

(When gedit (text editor) opens, insert this line near the top with other like entries. Specific line DOES NOT matter).

blacklist bcm43xx

After you click save, close the program.



**THIRD**: Paranoia! (Intermediate Skill Recommended) (Beginners may be able to skip this) 
[Reference ]("http://www.partha.com/kernel.html")for step: Due to I had problems in the past with FC6 (Fedora Core 6), I do this step to help.

Why delete what you are not sure you need?, so I just rename it (using mv)

In the terminal, type:

$ cd /lib/modules/2.6.20-16-generic/kernel/drivers/net/wireless/bcm43xx
$ sudo mv bcm43xx.ko bcm43xx.ko.old

**Important note!** it might be best to hit the Tab key when you get to /lib/modules/ due to you may have more then one kernel. It is HIGHLY recommended that you goto your most current one (being if it is a 2.6.20-15-generic or a 2.6.20-16-generic, choose the latter)

Next type in (in terminal window)

$ sudo depmod -a

I would bookmark this page in firefox, then reboot your system (if you are doing this from this tutorial now).


**FOURTH**: Lets get Automatix!

Automatix2 makes your life easy as an Ubuntu user, and is simply great, but if you live in the Unites States, it is not legal to enter the DVD decryption due to this may break laws.

Note: We are not covering this, but simply using a tools it provides (ndiswrapper) due to this is a faster, graphical frontend that you seem to only have to point and click.

goto [this link]("http://www.getautomatix.com/wiki/index.php?title=Installation#Easy_Direct_Installation") found at [http://www.getautomatix.com/wiki/index.php?title=Installation#Easy_Direct_Installation]("http://www.getautomatix.com/wiki/index.php?title=Installation#Easy_Direct_Installation")

Choose specifically which of the versions you have, and download it. The simple method is that firefox should select a default program (GDebi) which is fine to run with. 
If running it with GDebi doesen't work, download it to your desktop, minimize your window, and RIGHT CLICK and install by selecting "Open with "GDebi Installer", which (might) prompts you for password.

Let the installer do it's thing,  and once successfully installed, goto System tools in your Applications Menu (Applications >> System Tools >> Automatix) which might ask your password (yet again). Automatix2 Asks a yes or no question (about the DVD libraries mentioned at the beginning) which I click No (it will still proceed with some warning about stuff might not be initiallized etc etc.)

The window pops up for Automatix, then goto Drivers, and in the right window select (check the box) NDISWrapper, then click "Start" button in the Automatix window to begin. It might take a sec (depending on connection, but seems to be pretty fast. Once done, close the window.

**FIFTH**: Get & install driver

Now, we need to download a program that makes life easier. 
Type the following in a terminal:

$ cd ; sudo apt-get install cabextract -y ; mkdir ndis ; cd ndis

This returns you to your home directory (/home/(your username)), uses apt-get to install the tool (cabextract), and then makes a directory to keep the files we will be extracting for your WiFi card.

The driver I use seems to work fine is the Windows XP (32-bit) with no issues. Mine is found at [this link]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-41607-1&lc=en&cc=us&dlc=en&product=1841880&os=228&lang=en") (go down a little till you see the [download link]("ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe"). If you download it, save it to /home/(your username)/ndis or if you havent, type the following:

$ wget [ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)


Next, we need to extract the files, by typing:

$ cd ; cd ndis ; cabextract sp33008.exe

Now, you goto System in your upper task bar (System >> Administration >> Windows Wireless Drivers) which should (yet again) prompt you for your password. 
It will pop open a window "Wireless Network Drivers".
Click on "Install New Driver", select the "Location: None" in the "Select *inf *File" window, goto your ndis directory, and then click the bcmwl5.inf file (if not named the same, look for a .inf file, which (in my experience) there is only one). 

My Wifi Light usually promptly lights up with a blue light, and *POOF*, the mythic WiFi dilemma is solved. Goto connection manager, left click it and (if there are any near by) you should see networks available. I usually look to disconnect my wired connection, then select the WiFi network of choice and surf!. 


Hope this helps all!
RZ

---

### Post by kevdog on 2007-07-19
I see you put a lot of work in your guide and you should be commended for this, however there is no way I would recommend anyone install ndiswrapper via automatix or repository.  Ive been helping many, many people out on a daily basis and always recommend they actually download and compile from source.  There are various bugs (WPA is one I can think of off the top of my head), that are caused by some older ndiswrapper versions and various chipsets.

If you truly want to make this an informative guide I suggest you recommend compilation from source.  Another problem you need to deal with is that many people try to install ndiswrapper on a computer without an internet connection.  Pretty hard to install and use automatix without an internet connection.

---

### Post by ripperzane on 2007-07-19
> **kevdog said:**
> I see you put a lot of work in your guide and you should be commended for this, however there is no way I would recommend anyone install ndiswrapper via automatix or repository.  Ive been helping many, many people out on a daily basis and always recommend they actually download and compile from source.  There are various bugs (WPA is one I can think of off the top of my head), that are caused by some older ndiswrapper versions and various chipsets.

If you truly want to make this an informative guide I suggest you recommend compilation from source.  Another problem you need to deal with is that many people try to install ndiswrapper on a computer without an internet connection.  Pretty hard to install and use automatix without an internet connection.

True and agreed that NDISwrapper is buggy, but I am 1. posting my findings, and 2, giving the method I found works. This guide is not intended for the intermediate user, but also the Noob alike. Building from source does not always work, nor is it the easiest, even if the best.
3. The use of automatix is NOT the best method, as to easyubuntu is recommended due to that it installs without affecting your sources.list (according to the recent showing on the easyubuntu site).

I have had no issues with WPA, and am actually connected using WPA2 Personal on my WiFi Network. The thing I fiind is that since NDISwrapper is a tool to make the windows .inf file usable, not all results are the same. Doing this method, I see Ubuntu use my BCM43xx in a matter of seconds as opposed to rmmoding, then blacklisting, then using cabextract & ndiswrapper to install & get it up and running. In the end, I hope this is the fast way, that I know works for myself and others who have used it.

POINT: I agree it is best to install from source, but in actual, this may be the stopping point for many a person. I have been playing with many flavors since the earliest of Kernels, and do not want to have to figure it out, but to make it simply work.
Selah*
RZ

---

### Post by jglen490 on 2007-07-19
I agree with ripperzane on the downloading/compiling.  For the typical noob, the best solution is ti try the tools you have on hand.

When I got (finally) my Broadcom 4318-based wifi card to work, it was due to guidance found here in ubuntuforums, and a little bit of thought.  Rather than compiling ndiswrapper 1.8 from source, I found that version on my Kubuntu 6.06 LTS CD in a deb package.  I installed that deb  plus kwlan and wpa-supplicant with their respective packages.  From there is was a matter of "follow the dots" to a successful setup - that still works.

I blacklisted the bcm43xx driver that the kernel loaded, copied the applicable w2k driver from my card's install CD, installed that driver with ndiswrapper, installed the ndiswrapper module, setup kwlan along with wpa-supplicant, and I was off and running.

I'm no nob with respect to Linux, but I was in terms of wifi setup and the unique problems that wifi and Linux can have.  Use the tools you have - first, then dig deeper as a second choice.

---

