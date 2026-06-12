---
title: "Setting up Wireless"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by mckai on 2009-06-08
[COLOR=Red][B]EDIT: RESOLVED

[/B][/COLOR]Hello and thank you in advance for all the help =]

I'm posting this in frustration since I've been learning/googled/searched for what may be the problem affecting my access to internet - and I've been unsuccessful with utilizing any specific solution I've already read.

Recently I received a crashed Dell Inspiron 5150 laptop to play with. About ten years ago, my family had someone install linux on all of our computers; feeling nostalgic, I acquired Ubuntu 8.04 and installed it (after a bit of trouble). I was always fascinated with linux (but never learned enough to completely utilize it.)

Seeing that I have 'no network connection' - what should I do?

What information do you guys/gals need to help me specifically?

Thank you again. =]

---

### Post by keplerspeed on 2009-06-08
It depends on the wireless card, and what drivers are avaliable.

Firstly, go to system>administration>hardware drivers. See if a wireless driver appears there. If so, you will need an ethernet connection so you can install the wireless driver.

Otherwise, open a terminal (applications>accessories>terminal), and insert this code to see what wireless card it is.

```

lspci

```
And paste the output here if you cant see the card make and model there.

---

### Post by mckai on 2009-06-08
Ok. Ty again.

I found Broadcom B43 Wireless Driver, NVIDIA Accelerated Graphics Driver.

So how should I go about establishing an ethernet connection? I know - that probably sounds really silly - but I asked >_<.

I also typed in lspci - here is the response:

mckai@aries:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller

---

### Post by mckai on 2009-06-08
Oh jeez. Ethernet.. like as in 'paying' for internet access. u_u; There's no way I could utilize the wireless on this laptop to download anything of use for the other one?

---

### Post by keplerspeed on 2009-06-08
Ok, we need to Install the Broadcom B43 Wireless Driver. We will need to follow option 2 here:

[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

---

### Post by keplerspeed on 2009-06-08
I can walk you through this if required. Firstly, put the install cd in. Then in the terminal enter this:
```

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install b43-fwcutter

```

Then CANCEL when it wants to download firmware.

---

### Post by keplerspeed on 2009-06-08
To download firmware, enter this code (on the computer with working internet)
```

cd

```
```

wget http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o

```
```

wget http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2

```

Then use a USB and move those 2 files to the Dell 5150.

Then finally on the Dell enter this code:
```

cd
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo ifconfig wlan0 up

```

Wireless should be working now!

---

### Post by mckai on 2009-06-08
> **keplerspeed said:**
> I can walk you through this if required. Firstly, put the install cd in. Then in the terminal enter this:
```

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install b43-fwcutter

```Then CANCEL when it wants to download firmware.

How do you cancel? This is what happened to me - from your 'cancel' response, you anticipated the following:

[COLOR=DimGray][COLOR=Navy]mckai@aries:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [619f391dedf1a88ed5608b57a7c64dca-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
This disc is called: 
'Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)'
Copying package lists...gpgv: Signature made Tue 22 Apr 2008 04:34:19 PM PDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
Unmounting CD-ROM...
Repeat this process for the rest of the CDs in your set.[/COLOR]
[/COLOR]


[COLOR=Navy]mckai@aries:~$ sudo aptitude update
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-en_US
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg                       
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Translation-en_US            
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Translation-en_US      
  Could not resolve 'archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                       
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US            
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US      
  Could not resolve 'security.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release.gpg                        
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
  Could not resolve 'archive.canonical.com'
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
  Could not resolve 'archive.canonical.com'
Reading package lists... Done            



mckai@aries:~$ sudo aptitude install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following partially installed packages will be configured:
  b43-fwcutter 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up b43-fwcutter (1:011-1) ...
--18:53:16--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
           => `wl_apsta-3.130.20.0.o'
Resolving downloads.openwrt.org... failed: Name or service not known.
dpkg: error processing b43-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 b43-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up b43-fwcutter (1:011-1) ...
--18:53:17--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
           => `wl_apsta-3.130.20.0.o'
Resolving downloads.openwrt.org... failed: Name or service not known.
dpkg: error processing b43-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 b43-fwcutter
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      [/COLOR]

Also to download the firmware, how will  I enter the code? It's a windows vista laptop that I'm on. Shall I do a search for these:

[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)

[http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)

---

### Post by mckai on 2009-06-09
Ok so I think I probably tried too many things before I tried these solutions of yours. I'm installing ubuntu once more and will then try what you've laid out for me. Thank you for all the help =]

---

### Post by mckai on 2009-06-09
Complete success! Thank you. It was mainly user error lol. I typed in something wrong and that was that. I'm posting from the dell!

Now to figure out if my comp is alright with the 371 updates. O_o

---

