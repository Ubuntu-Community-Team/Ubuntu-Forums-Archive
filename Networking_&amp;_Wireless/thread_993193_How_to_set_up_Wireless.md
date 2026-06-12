---
title: "How to set up Wireless?"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by Angry Dog on 2008-11-25
I have just installed Ubuntu 8.10 onto my pc!

I am wanting to set up the wireless side of it.

I am very new to Ubuntu so please be gentle!

---

### Post by Ayuthia on 2008-11-25
> **Angry Dog said:**
> I have just installed Ubuntu 8.10 onto my pc!

I am wanting to set up the wireless side of it.

I am very new to Ubuntu so please be gentle!

Can you go into the Terminal and post the results of:
```
lspci -nn
```This will help us see what wireless card you have.  From there, we can help provide some options.

---

### Post by Angry Dog on 2008-11-25
Hi,

This is the line with the wireless card info on.


00:0e.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

Thanks

---

### Post by Ayuthia on 2008-11-25
> **Angry Dog said:**
> Hi,

This is the line with the wireless card info on.


00:0e.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

Thanks

Have you tried using the option in System->Administration->Hardware Drivers?  There should be an option for the b43 Broadcom driver.  You will need a working internet connection in Ubuntu though.  If you don't have a working connection, you can try this guide:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

---

### Post by Angry Dog on 2008-11-25
didnt seem to work?

Got this:

mike@Linux:~$ sudo aptitude install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
The following NEW packages will be installed:
  b43-fwcutter 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/16.3kB of archives. After unpacking 102kB will be used.
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package b43-fwcutter.
(Reading database ... 99820 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_011-4ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:011-4ubuntu1) ...
--2008-11-25 22:35:58--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `downloads.openwrt.org'
dpkg: error processing b43-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 b43-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up b43-fwcutter (1:011-4ubuntu1) ...
--2008-11-25 22:35:59--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `downloads.openwrt.org'
dpkg: error processing b43-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 b43-fwcutter
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done

---

### Post by Ayuthia on 2008-11-25
That is odd.  Are you able to connect to other sites?  You might try the manual process in my previous post and download the files from another computer.

---

### Post by Angry Dog on 2008-11-25
I cant connect to the web at all.

that was using the CD option.

How do you do that code thing?  I will paste in the entire text and then that way it'll be clearer?

Its an EDUP card FYI.

---

### Post by Ayuthia on 2008-11-25
> **Angry Dog said:**
> I cant connect to the web at all.

that was using the CD option.

How do you do that code thing?  I will paste in the entire text and then that way it'll be clearer?

Its an EDUP card FYI.

You can use the # button that is found at the top of the edit window when you are typing your post.

As for the CD option, don't have the system download the firmware for you.  It will fail because you don't have access to the internet.

---

### Post by Angry Dog on 2008-11-25
```
mike@Linux:~$ sudo apt-cdrom add
[sudo] password for mike: 
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [ac20a1ac35626cb607897968f3dd2440-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
This disc is called: 
'Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)'
Copying package lists...gpgv: Signature made Wed 29 Oct 2008 23:24:11 GMT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
Unmounting CD-ROM...
Repeat this process for the rest of the CDs in your set.
W: Skipping non-exisiting file /cdrom/dists/intrepid/main/binary-i386/Packages
W: Skipping non-exisiting file /cdrom/dists/intrepid/restricted/binary-i386/Packages
mike@Linux:~$ sude aptitude update
bash: sude: command not found
mike@Linux:~$ sud0 aptitude update
bash: sud0: command not found
mike@Linux:~$ sudo aptitude update
Err http://security.ubuntu.com intrepid-security Release.gpg
  Could not resolve &#8216;security.ubuntu.com&#8217;
Err http://security.ubuntu.com intrepid-security/main Translation-en_GB
  Could not resolve &#8216;security.ubuntu.com&#8217;
Err http://security.ubuntu.com intrepid-security/restricted Translation-en_GB
  Could not resolve &#8216;security.ubuntu.com&#8217;
Err http://security.ubuntu.com intrepid-security/universe Translation-en_GB
  Could not resolve &#8216;security.ubuntu.com&#8217;
Err http://security.ubuntu.com intrepid-security/multiverse Translation-en_GB
  Could not resolve &#8216;security.ubuntu.com&#8217;
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Translation-en_GB
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Translation-en_GB
Err http://gb.archive.ubuntu.com intrepid Release.gpg
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err http://gb.archive.ubuntu.com intrepid/main Translation-en_GB
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err http://gb.archive.ubuntu.com intrepid/restricted Translation-en_GB
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err http://gb.archive.ubuntu.com intrepid/universe Translation-en_GB
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err http://gb.archive.ubuntu.com intrepid/multiverse Translation-en_GB
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err http://gb.archive.ubuntu.com intrepid-updates Release.gpg
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err http://gb.archive.ubuntu.com intrepid-updates/main Translation-en_GB
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err http://gb.archive.ubuntu.com intrepid-updates/restricted Translation-en_GB
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err http://gb.archive.ubuntu.com intrepid-updates/universe Translation-en_GB
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err http://gb.archive.ubuntu.com intrepid-updates/multiverse Translation-en_GB
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Reading package lists... Done            

mike@Linux:~$ sudo aptitude install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
The following partially installed packages will be configured:
  b43-fwcutter 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up b43-fwcutter (1:011-4ubuntu1) ...
--2008-11-25 23:19:14--  http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `downloads.openwrt.org'
dpkg: error processing b43-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 b43-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up b43-fwcutter (1:011-4ubuntu1) ...
--2008-11-25 23:19:15--  http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `downloads.openwrt.org'
dpkg: error processing b43-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 b43-fwcutter
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done


```

It doesnt give me the option for a download?

---

### Post by Angry Dog on 2008-11-25
If I look at the hardware drivers section, it lists the driver there, but it wont "Activate"

---

### Post by Angry Dog on 2008-11-25
[IMG]http://img.photobucket.com/albums/0603/sapphymike/Screenshot-HardwareDrivers.jpg[/IMG]

---

### Post by Ayuthia on 2008-11-25
> **Angry Dog said:**
> If I look at the hardware drivers section, it lists the driver there, but it wont "Activate"

Correct.  You will not be able to activate it through Hardware Drivers because you do not have a working connection in Ubuntu.  You will need to download the firmware from an OS that has an internet connection and then copy it back to your desktop in Ubuntu. From there, you will need to run b43-fwcutter to cut the necessary portions for the driver.

If you need some help with this, please start with getting the firmware from my first post in this thread and copy the file to your desktop.  Once that is complete, let us know.  If you are not for sure what files you need, just let me know.

---

### Post by Angry Dog on 2008-11-25
This is what I got.

```
mike@Linux:~$ sudo dpkg -i b43-fwcutter_011-4ubuntu1_i386.deb
(Reading database ... 99829 files and directories currently installed.)
Preparing to replace b43-fwcutter 1:011-4ubuntu1 (using b43-fwcutter_011-4ubuntu1_i386.deb) ...
Unpacking replacement b43-fwcutter ...
Setting up b43-fwcutter (1:011-4ubuntu1) ...
--2008-11-25 23:58:49--  http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `downloads.openwrt.org'
dpkg: error processing b43-fwcutter (--install):
 subprocess post-installation script returned error exit status 1
Processing triggers for man-db ...
Errors were encountered while processing:
 b43-fwcutter
mike@Linux:~$ 


```

---

### Post by Ayuthia on 2008-11-25
> **Angry Dog said:**
> This is what I got.

```
mike@Linux:~$ sudo dpkg -i b43-fwcutter_011-4ubuntu1_i386.deb
(Reading database ... 99829 files and directories currently installed.)
Preparing to replace b43-fwcutter 1:011-4ubuntu1 (using b43-fwcutter_011-4ubuntu1_i386.deb) ...
Unpacking replacement b43-fwcutter ...
Setting up b43-fwcutter (1:011-4ubuntu1) ...
--2008-11-25 23:58:49--  http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `downloads.openwrt.org'
dpkg: error processing b43-fwcutter (--install):
 subprocess post-installation script returned error exit status 1
Processing triggers for man-db ...
Errors were encountered while processing:
 b43-fwcutter
mike@Linux:~$ 


```

Can you try the following:
```
which b43-fwcutter
```
If it returns /usr/bin/b43-fwcutter, that is ok.  We can reconfigure it afterwards.

---

### Post by Angry Dog on 2008-11-25
It returns /usr/bin/b43-fwcutter

---

### Post by Ayuthia on 2008-11-25
> **Angry Dog said:**
> It returns /usr/bin/b43-fwcutter

Good.  I am assuming that you have already downloaded the following files to your Desktop:
```
http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
```

You can then do the following:
```
cd
cd Desktop
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.150.10.5.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo modprobe -r b43 ssb
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```

Most of these commands will not return anything.

---

### Post by Angry Dog on 2008-11-26
Hi,

I didnt have those files no. When I downloaded the B43 file from the earlier site, I didnt see these files?

Thanks for all your help up to now, really appreciated!

I wont be able to get to my linux pc for another 8 and a half hours mind :(

Will it work with WPA?

You seem to know your stuff with this Wireless lark in Linux! :)

---

### Post by Ayuthia on 2008-11-26
> **Angry Dog said:**
> Hi,

I didnt have those files no. When I downloaded the B43 file from the earlier site, I didnt see these files?

Thanks for all your help up to now, really appreciated!

I wont be able to get to my linux pc for another 8 and a half hours mind :(

Will it work with WPA?

You seem to know your stuff with this Wireless lark in Linux! :)

Well, if this works it should be able to connect with WPA, however, it would be best if you could test it without encryption just to be sure that it can connect.  I will have to admit that some of the 4318 cards have had problems with the b43 driver, but they have gotten better in 8.10.  If this does not work, there is the ndiswrapper option.  It is just easier to try this option first because ndiswsrapper requires some configuration.

---

### Post by Angry Dog on 2008-11-26
You are a genius!

Thank you sooooo much :)

Its working like a dream!

Huge thanks!!!!!

---

### Post by roy bowman on 2008-11-26
> **Angry Dog said:**
> I have just installed Ubuntu 8.10 onto my pc!

I am wanting to set up the wireless side of it.

I am very new to Ubuntu so please be gentle!
Title: Wireless want-to-be
Re: [SOLVED] How to setup Wireless? (Response)
you need to get two pieces of hardware (a.)wireless - g broadband router which is pretty good for home use and (b.) the wireless adapter which is the adapter which plugs into your usb port on a laptop;it is  shaped like a small paint scraper with a five foot wire attached to it.If you are setting up a desktop pc, then choose an appropriate wireless card, Think antennae! Companies like lynksys and belkin offer these products. These hard ware items come packaged with directions and pictures on how to set them up.//If your computer is relatively new, it will probably meet system requirements which are also reviewed on the hardware packages so try to understand there importance. Some background info on the hardware; they send and receive electrical signals in established frequency ranges. These devices, which you have or are about to purchase communicate with each other as transceivers which can send (upload) and receive (download) data thru the air as electrical signals according to an agreed upon standard established by electrical engineer groups. All you are going to do is plug these hardware devices up so they can communicate with each other. A lot of decisions have been made for you so that the devices will work. On the outside chance that there are mechanical problems all ways keep the receipts of your purchases. Also your Internet Provider (IP) will continue to be a partner in your efforts. Good luck.

---

### Post by Angry Dog on 2008-11-26
err..

its all set up.

im typing from my linux box now! LOL

---

### Post by cliffskoog on 2009-03-26
WOW.
I had a very similar problem (8.10): an EDUP wireless card with bcmwl5.inf file on its win install disk and various other bcm43 files too. These mysterious instructions certainly did the trick.
Thanks so much!

---

### Post by Goodbytes on 2009-03-27
> **Ayuthia said:**
> 
You can then do the following:
```
cd
cd Desktop
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.150.10.5.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo modprobe -r b43 ssb
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```

Most of these commands will not return anything.


Thank you Ayuthia! I'm setting up an Ubuntu Server 8.04 box, and I've had a very educational experience getting wifi drivers installed on a command-line-only system. (Time limits just make it that much more fun.) 

Anyway. Following your example here, I got a new Linksys WMP54gs card working on my Biostar T6100 motherboard, but ran into one difference. On the second b43-fwcutter line (w/ --unsupported) I got a three-line error, something about the firmware was too new, followed by two url's: one for an older firmware, and one that appeared to be for b43-fwcutter itself. I don't have a copy of the urls it gave, but I wgot the older firmware and installed it in the same fashion. The only difference was that I left off the --unsupported option. 

Worked perfectly, thanks again. :)

-- Goodbytes

---

### Post by airdrummer on 2009-03-28
i'd installed the broadcom firmware using b43-fwcutter, and my wpc54gs was seeing my WAP (wrt54g) but couldn't connect: i kept entering my WPA key, network mgr kept asking me to enter it, over&over:-(

i tried turning off all security, but n/w mgr wanted me to enter a key, with nowhere to enter it:-P

so i found this thread, did the modprobe & ifconfig, & hallafukkinlooyah i'm connected...for about 2mins:

PING google.com (209.85.171.100) 56(84) bytes of data.
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=1 ttl=233 time=98.8 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=2 ttl=233 time=101 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=3 ttl=233 time=104 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=4 ttl=233 time=323 ms
^C
--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3011ms
rtt min/avg/max/mdev = 98.843/157.064/323.372/96.036 ms

ad@marcia-laptop:~$ ping google.com
ping: unknown host google.com

now i'm back to constant reconnects...

i'm running xubuntu/8.10 on an old dell latitude p3/256mb for my bro-in-law's wife...it's gotta just work, & they can't afford an apple...and it doesn't have an ethernet i'f, so i gotta sneakernet via CDs

Linux marcia-laptop 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux

and people wonder why linux doesn't take over;-}

---

### Post by airdrummer on 2009-03-28
after reboot (system locked up after burning cd...did i mention all the phantom clicks while mousing w/the trackpad)-? i was able to connect again, but it dropped in <1min...here's the relevant part of dmesg:

[  286.620232] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  286.728041] Registered led device: b43-phy0::tx
[  286.728041] Registered led device: b43-phy0::rx
[  286.728738] Registered led device: b43-phy0::radio
[  286.916316] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  287.028039] Registered led device: b43-phy0::tx
[  287.028039] Registered led device: b43-phy0::rx
[  287.029167] Registered led device: b43-phy0::radio
[  287.216304] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  287.323623] Registered led device: b43-phy0::tx
[  287.324036] Registered led device: b43-phy0::rx
[  287.324036] Registered led device: b43-phy0::radio
[  294.738014] wlan0: authenticate with AP 00:1a:70:6e:31:30
[  294.744593] wlan0: authenticated
[  294.744737] wlan0: associate with AP 00:1a:70:6e:31:30
[  294.748037] wlan0: RX AssocResp from 00:1a:70:6e:31:30 (capab=0x411 status=0 aid=3)
[  294.748037] wlan0: associated
[  294.750811] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  305.120113] wlan0: no IPv6 routers present
[  348.001889] __ratelimit: 23425 callbacks suppressed
[  348.002002] b43-phy0 ERROR: PHY transmission error
[  348.002177] b43-phy0 ERROR: PHY transmission error
[  348.002332] b43-phy0 ERROR: PHY transmission error
[  348.002485] b43-phy0 ERROR: PHY transmission error
[  348.002639] b43-phy0 ERROR: PHY transmission error
[  348.002796] b43-phy0 ERROR: PHY transmission error
[  348.002952] b43-phy0 ERROR: PHY transmission error
[  348.003107] b43-phy0 ERROR: PHY transmission error
[  348.003259] b43-phy0 ERROR: PHY transmission error
[  348.003415] b43-phy0 ERROR: PHY transmission error
[  348.260261] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  348.368043] Registered led device: b43-phy0::tx
[  348.368043] Registered led device: b43-phy0::rx
[  348.369142] Registered led device: b43-phy0::radio
[  348.556326] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  348.664043] Registered led device: b43-phy0::tx
[  348.664043] Registered led device: b43-phy0::rx
[  348.664043] Registered led device: b43-phy0::radio
[  348.892239] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

and it continues ad nauseum:-(

---

### Post by oneearth on 2009-04-18
thanks Ayuthia for your expertise.

> You can then do the following:
Code:
.
cd
cd Desktop
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.150.10.5.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo modprobe -r b43 ssb
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan



for my dell latitude d505 running a broadcom bcm4320 rev 02 chipset, i didn't do the broadcom-wl-4.150 part of your procedure, just the b43-fwcutter parts.

i was delighted when the iwlist scan listed some wireless networks!

now that the wireless was working, being a noob, i didn't even know how to select and connect to a wireless network. finally i clicked the little network icon on the bottom taskbar and it showed me the available networks. i let out a gleeful shout when it actually connected!

thanks for all your hard work and generosity in using your time to respond to some of our hapless questions. it helps spread ubuntu and linux to the community. ubuntu/linux without wireless is a major obstacle to more folks adapting the os. so any help with wireless drivers is really making a big difference to the spread of ubuntu/linux.

---

### Post by DiscoStu570 on 2009-11-05
Big ups to Ayuthia for solving this one, I know exactly enough about Ubuntu to wreck up my wireless connection and following your instructions fixed it.  +1

---

### Post by canadiandude007 on 2010-08-15
[QUOTE=oneearth;7093245]

Thanks for your assistance as this also worked for Ubuntu 10.4 using an iMac with Broadcom wireless.  Nice work!:D

---

### Post by NiNE_ on 2010-09-30
> **Ayuthia said:**
> Good.  I am assuming that you have already downloaded the following files to your Desktop:
```
http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
```You can then do the following:
```
cd
cd Desktop
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.150.10.5.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo modprobe -r b43 ssb
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```Most of these commands will not return anything.

Wow thanks dude !!! You're the best, I just had the same problem as the OP and this thing what you wrote fixed my net, thanks a lot bro!!

---

