---
title: "broadcom 4309 not recognized"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by greyash99 on 2007-01-11
my broadcom wireless card is no longer recognized.  It was recognized in dapper, but it never worked.  can someone tell me how to get it recognized?

---

### Post by greyash99 on 2007-01-11
bump

---

### Post by TheFourthOne on 2007-02-11
TheFourthOne;2139418]Hey!

I have been looking all over the place, reading tuts trying different things with no success. I am running a Dell Latitude D600 with the BCM 4309 chipset. I DID FINALLY get it working!
Go [here]("http://products.wildpackets.com/?v=bs2h5ampbyiw0049&s=1") that should download the 4309 driver (it is the driver specifically for the 4309) open it up and copy the .info and the .sys file to your desktop. then go [HERE]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Ndiswrapper_for_Broadcom_43xx_wireless_chipset")
and download the file they offer (keep this page up too, it's the one you'll use to follow directions) after you download the file open it up (don't extract) and copy the 32 bit file to the desktop. Open that file up and replace the .info and .sys files inside with the ones you have on your desktop. then replace the 32 bit file into the .tar.gz file you downloaded and continue following the directions in the ubuntu starter guide. Note this is for 32 bit, but I think if you find the 64 bit driver you could follow the same principal. Also I'm running Edgy, but if ndiswrapper works in other distros I don't see why it wouldn't work for anyone else. Hope it helps! :)

---

### Post by Feenix3k on 2008-04-11
> **greyash99 said:**
> my broadcom wireless card is no longer recognized.  It was recognized in dapper, but it never worked.  can someone tell me how to get it recognized?

I used the BCM 4318 driver. I had a/b/g full working order. The file bcm4318.all.tar.gz   When I used wl_apsta.o it never worked right in any version of Ubuntu. I just wish the bcm4318.all.tar.gz work in the other versions like 7.10

The code I got here in the forums. The directions I used follow:

 HOWTO/SCRIPT: Broadcom 4318 Wireless Cards 

About

This HOWTO is for people who have a Broadcom 4318 Wireless card in their laptop. This card can sometimes be a bit  difficult to setup, so I have provided a working method (for me, anyway).

To check if you have a Broadcom 4318 Card, open up the terminal (click the Applications button, then Accessories, and then Terminal) and run (just copy and paste the code from the code boxes throughout the HOWTO [in the terminal, this is done by right click anywhere and clicking paste, ctrl+v doesn't work])
Code:
lspci | grep Broadcom\ Corporation
If your output looks similar to 
Code:
0000:05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
or you can see the string BCM4318 in the output, then this should work for you.

Please note that this was really designed to be run on a very fresh install, right after Ubuntu has come up for the first time. It is mostly likely to work then. If you have tried other attempts at making this card work, I have no promises for you, but it only takes two minutes, so it is worth a shot (most people can get it to work, even on a not-so-fresh install).

The point of this HOWTO is to make it as simple as possible (not to educate people - if you want to know how this works, open the script and read it) for people who have just installed Ubuntu for the first time, so I wrote a script and have provided a set of drivers that worked for me. Not all drivers will work with ndiswrapper, so please use the ones I have provided.

The script requires no internet connection after it is downloaded...all required files are on the CD you installed Ubuntu with, and the package manager should recognize this.

If you post for help, please post the log file, which can be found on your Desktop after you run the script.

Process for Dapper and Edgy (see Fiesty in troubleshooting)
1.Put the CD that you installed Ubuntu with in the CD drive.
2.Download this file to your Desktop (the Firefox default, so if you haven't changed it, that's where it went/will go).
3.Open a terminal (click the Applications button, then Accessories, and then Terminal)
4.Change the current directory to the desktop (copy and paste the following commands exactly into your terminal by right clicking anywhere on the terminal and clicking paste)
Code:
cd ~/Desktop
5.Extract the compressed file
Code:
tar -xf bcm4318*.tar.gz
6.Run the script, which will install ndiswrapper on your system, and set it up.
Code:
sudo ./ndiswrapper_setup
7.Use the internet (you will have to open the System menu at the top of the screen, go to Administration, and then click Networking. Configure the interface eth1 or wlan0, and connect to your wifi network)
8.If you are an Acer user, you will need to use the acerhk driver.
9.If it doesn't work, reboot.
10.If that doesn't work, read the troubleshooting section below.
11.If you still can't make it work, try reading this post by The Raven, which is so long I can't even fit it in here without doubling the length of the post

---

