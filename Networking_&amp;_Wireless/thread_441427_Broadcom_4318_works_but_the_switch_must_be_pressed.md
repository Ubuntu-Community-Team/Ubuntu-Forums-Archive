---
title: "Broadcom 4318 works but the switch must be pressed first"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by gilang27 on 2007-05-12
I have Compaq V5000z with AMD Sempron, it's got Broadcom 4318 and I am using ndiswrapper for the driver because it's faster than the broadcom driver itself. Now, everything can be used, but it's kind of boring, because I have to press tthe WLAN switch button twice times in order to get the wireless working. If I didn't press it twice, the network was still detected, but then I couldn't connect. Anybody know why?:popcorn: 

These are my steps:

Dapper and Edgy (and Feisty with ndiswrapper)
1.Put the CD that you installed Ubuntu with in the CD drive.
2.Download this file to your Desktop (the Firefox default, so if you haven't changed it, that's     where it went/will go).
3.Open a terminal (click the Applications button, then Accessories, and then Terminal)
4.Change the current directory to the desktop (copy and paste the following commands exactly into your terminal by right clicking anywhere on the terminal and clicking paste)

Code:
cd ~/Desktop

4.Extract the compressed file
Code:
tar -xf bcm4318*.tar.gz

5.Run the script, which will install ndiswrapper on your system, and set it up.
Code:
sudo ./ndiswrapper_setup

6.Use the internet (you will have to open the System menu at the top of the screen, go to Administration, and then click Networking. Configure the interface eth1 or wlan0, and connect to your wifi network)

7.If it doesn't work, reboot.
8.If that doesn't work, read the troubleshooting section below.

9.If you are having issues, try running, in this order, one at a time:
Code:
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo ifdown eth1
sudo ifup eth1
sudo dhclient

that's what I did, but the WLAN switch has to be pressed twice times..anyone please help me....#-o

---

