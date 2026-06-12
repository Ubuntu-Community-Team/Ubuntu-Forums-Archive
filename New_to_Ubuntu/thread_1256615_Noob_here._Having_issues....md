---
title: "Noob here. Having issues..."
date: 2009-09-02
forum: New to Ubuntu
---

### Post by see.unseen83 on 2009-09-02
Alright folks, so i am running 8.10 on a acer aspire 3000. i've managed to get most everything up and running well and i love it. ubuntu is awesome. only bummer is that i think i can't get a driver for my graphics card. i really don't want to go back to windows, but i kind of really need that working.

i typed "lspci" in terminal and got this:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

now, from what i understand this sis graphics card does not have a linux friendly driver. i even checked their website for the driver and it wasn't there.

 is this true? am i really going to have to go back to the darkside?

thanks for any and all help,

jake

---

### Post by lotsofish on 2009-09-02
There is a driver available, but it's not from SIS. 
Look at this page: [http://www.winischhofer.net/linuxsisvga.shtml](http://www.winischhofer.net/linuxsisvga.shtml)

Looks like there was a free version and a premium version, with extra features, but for a fee. The download page says development has stopped, so the source for the premium version is available, along with the source and binaries for the free version.

The binaries are available up to X.Org version 7.1, which is going to be a couple versions behind for you, but you could try it. That would be the easiest option. Otherwise if that doesn't work or you want the premium features, you will have to compile the premium version from source, which probably isn't as hard as it sounds. There's most likely a readme file that tells you how to do it.

---

### Post by halitech on 2009-09-02
what might be easier is getting a supported card for your system and installing that. Looking at the output, I would guess you should have either an AGP slot or a PCI-e slot. Either way, you can pick up a new card for a few dollars that is supported or a used one for less. I would probabl suggest Nvidia as they have better support for older cards.

---

### Post by see.unseen83 on 2009-09-02
wow! thanks a lot everyone! this is my first thread so it's amazing to see people being so helpful. i've been a member of the forums fo a little while now but just got ubuntu up on my laptop since i recently had a lull in the need to run cs3. mainly photoshop and illustrator. which i'm thinking of running in vmware. right choice? anyway...

lotsofish:
i'm going to see if i can get the older binaries off of that link. when i get those binaries, what do i do with them? sorry. very, very noob. 

halitech:
what do you think would be a good choice for a new card?

---

### Post by halitech on 2009-09-02
if you are planning on sticking with 8.10 then pretty much any card should work better then the SiS card. If you want to upgrade to 9.04 (or newer) then stay away from ATI and get a decent Nvidia card. Do you know if you have an AGP or PCI-E slot?

---

### Post by theozzlives on 2009-09-02
> **halitech said:**
> if you are planning on sticking with 8.10 then pretty much any card should work better then the SiS card. If you want to upgrade to 9.04 (or newer) then stay away from ATI and get a decent Nvidia card. Do you know if you have an AGP or PCI-E slot?

It's a laptop!

---

### Post by halitech on 2009-09-02
d'oh, missed that in the OPs second post, guess upgrading the video card isn't really an option then.

---

### Post by see.unseen83 on 2009-09-02
haha. yeah, not an option. that's funny that i even asked. but then again, i have taken this thing apart and put it back together. is the card inside this thing most likely a "plug in" type thing?

---

### Post by L33Tsauce on 2009-09-02
> **see.unseen83 said:**
> Alright folks, so i am running 8.10 on a acer aspire 3000. i've managed to get most everything up and running well and i love it. ubuntu is awesome. only bummer is that i think i can't get a driver for my graphics card. i really don't want to go back to windows, but i kind of really need that working.

i typed "lspci" in terminal and got this:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

now, from what i understand this sis graphics card does not have a linux friendly driver. i even checked their website for the driver and it wasn't there.

 is this true? am i really going to have to go back to the darkside?

thanks for any and all help,

jake




I had same problem but i just switched to 9.04 :D It makes everything way easier i could not find my drivers at all but on 9.04 when i went into hardware and drivers it listed it :DDDDD

---

### Post by see.unseen83 on 2009-09-02
sounds like a good option. did you have the same card as well?

---

### Post by lotsofish on 2009-09-02
Here is the download page: [http://www.winischhofer.net/linuxsispart4.shtml#download](http://www.winischhofer.net/linuxsispart4.shtml#download)  

I didn't read down far enough, but under section 5, there is a repository for Debian/Ubuntu. Since you have a newer version of X.Org than he has binaries for (Ubuntu 8.10 uses X.Org 7.4 and he has up to X.org 7.1) I would suggest using the from source option. You can ignore the part about the GPG keys.

1) Open System > Administration > Software Sources
2) Under third-party software, click add, then enter 'deb-src [http://www.winischhofer.net/sis/debian/unstable](http://www.winischhofer.net/sis/debian/unstable) ./'
3) Close the Software Sources box and open a Terminal (Applications > Accessories > Terminal)
4) Type 'apt-src build sisctrl'

I've never tried installing software in this method, so someone else may be able to confirm this. The page says it will create a .deb file when using this method. All you have to do then is double click the .deb from Nautilus, and then tell it to install. 

After you get that installed, you may still be in for some Xorg.conf editing to tell it to use your driver, but try to get the driver installed first and we can go from there.

---

### Post by lotsofish on 2009-09-02
> **see.unseen83 said:**
> haha. yeah, not an option. that's funny that i even asked. but then again, i have taken this thing apart and put it back together. is the card inside this thing most likely a "plug in" type thing?

Not likely. They are usually built into the mainboard.

---

### Post by see.unseen83 on 2009-09-03
alright, i did what you said about getting 'deb-src [http://www.winischhofer.net/sis/debian/unstable](http://www.winischhofer.net/sis/debian/unstable) ./' into my third party software sources. then i typed 'apt-src build sisctrl' in terminal and got:

'The program 'apt-src' is currently not installed.  You can install it by typing:
sudo apt-get install apt-src
bash: apt-src: command not found'

and so i did... holy hell...this came out...

'Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic mysql-common
  libmysqlclient15off dkms virtualbox-ose-source cabextract xutils-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  build-essential dpkg-dev g++ g++-4.3 libapt-pkg-perl libstdc++6-4.3-dev
Suggested packages:
  debian-keyring g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg
  libstdc++6-4.3-doc
The following NEW packages will be installed:
  apt-src build-essential dpkg-dev g++ g++-4.3 libapt-pkg-perl
  libstdc++6-4.3-dev
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 6229kB of archives.
After this operation, 21.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ftp.usf.edu](http://ftp.usf.edu) intrepid/universe libapt-pkg-perl 0.1.22build1 [88.8kB]
Get:2 [http://ftp.usf.edu](http://ftp.usf.edu) intrepid-updates/main dpkg-dev 1.14.20ubuntu6.2 [613kB]
Get:3 [http://ftp.usf.edu](http://ftp.usf.edu) intrepid/universe apt-src 0.25.1-0.1 [36.4kB]         
Get:4 [http://ftp.usf.edu](http://ftp.usf.edu) intrepid-updates/main libstdc++6-4.3-dev 4.3.2-1ubuntu12 [1354kB]
Get:5 [http://ftp.usf.edu](http://ftp.usf.edu) intrepid-updates/main g++-4.3 4.3.2-1ubuntu12 [4128kB]
Get:6 [http://ftp.usf.edu](http://ftp.usf.edu) intrepid-updates/main g++-4.3 4.3.2-1ubuntu12 [4128kB]
Get:7 [http://ftp.usf.edu](http://ftp.usf.edu) intrepid/main g++ 4:4.3.1-1ubuntu2 [1444B]            
Get:8 [http://ftp.usf.edu](http://ftp.usf.edu) intrepid/main build-essential 11.4 [7172B]            
Fetched 3508kB in 40min8s (1457B/s)                                            
Selecting previously deselected package libapt-pkg-perl.
(Reading database ... 140261 files and directories currently installed.)
Unpacking libapt-pkg-perl (from .../libapt-pkg-perl_0.1.22build1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.20ubuntu6.2_all.deb) ...
Selecting previously deselected package apt-src.
Unpacking apt-src (from .../apt-src_0.25.1-0.1_all.deb) ...
Selecting previously deselected package libstdc++6-4.3-dev.
Unpacking libstdc++6-4.3-dev (from .../libstdc++6-4.3-dev_4.3.2-1ubuntu12_i386.deb) ...
Selecting previously deselected package g++-4.3.
Unpacking g++-4.3 (from .../g++-4.3_4.3.2-1ubuntu12_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.3.1-1ubuntu2_i386.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4_i386.deb) ...
Processing triggers for man-db ...
Setting up libapt-pkg-perl (0.1.22build1) ...
Setting up dpkg-dev (1.14.20ubuntu6.2) ...
Setting up apt-src (0.25.1-0.1) ...
Setting up g++-4.3 (4.3.2-1ubuntu12) ...
Setting up libstdc++6-4.3-dev (4.3.2-1ubuntu12) ...
Setting up g++ (4:4.3.1-1ubuntu2) ...

Setting up build-essential (11.4) ...

hope this didn't screw anything up. looked like some autoated installations and updates. so anyway, after all that, i typed in 'apt-src build sisctrl' again and got:

E: Not installed

very sorry if my noob-ness is annoying. i just don't know what i'm doing wrong.

thanks again.

---

