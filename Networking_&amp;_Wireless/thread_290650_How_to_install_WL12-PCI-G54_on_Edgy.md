---
title: "How to install WL12-PCI-G54 on Edgy"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by GS2 on 2006-11-01
My first post, and a long one, but after a recent install of Ubuntu I thought I would share this with you all. Comments/criticism are welcome, for alterations or any other reason.

This is a how-to guide, and is compiled from many sources - which can confuse n00bs like myself to Ubuntu.
It took me many hours to get the wifi setup, but it is running fine now after many reboots.
To save users having to do the constant searching this is the steps I took.
Please note this was for on a clean install of Ubuntu Edgy

My setup was as follows: 
1 Desktop with fresh install of Ubuntu Edgy; Wireless card: Buffalo WL12-PCI-G54 wireless 54Mbps Desktop PCi Adapter
1 laptop with internet access (Windoze OS, sorry but couldn't 'get' the drivers any other way..yet)
1 usb stick
1 Ubuntu Edgy Os cd (this is needed for ndiswrapper)

1)First ensure your PCI card **is not installed** in the desktop system. Boot up your Ubuntu desktop PC and sign in.

2)Using the otherlaptop/pc with internet access I visited the following page:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

Using the search function **Buffalo**I found the following info for the card:
> Card: Buffalo Tech WLI2-PCI-G54

    * Chipset: Buffalo BCM94306 (rev 03)
    * pciid: 14e4:4320
    * Driver: [ftp://ftp.dell.com/network/R81433.EXE](ftp://ftp.dell.com/network/R81433.EXE)
    * Other: Use the .inf in the AR directory. Works with ndiswrappers 0.11 and RHEL 3.
    * Other: Ubuntu 5.04 (Hoary), ndiswrapper 1.0rc2, dell drivers from file R81433.EXE. I used the bcmwl5, not bcmwl5a drivers in the AR directory, not sure of the difference. No luck until I editted *every* .conf file in /etc/ndiswrapper/bcmwl5/, replacing RadioState|1 with RadioState|0. Now it appears to be working perfectly on an open network. 

The important part is the drivers, without the correct ones ndiswrapper will not be able to 'run' the wireless card.
So I downloaded the drivers from the dell site, and installed the package on a Windows system (the laptop) by double clicking on the R81433.exe file.
They were placed in the following directory:
C:\Dell\Drivers\R81433\

Once the files have been copied to this directory, navigate to 

C:\Dell\Drivers\R81433\AR\

and copy the following Windows drivers to the USB stick:

bcmwl5 (a Setup Information file which will show as bcmwlf.inf in Ubuntu)
bcmwl5 (A Windows system file which will show up as bcmwl5.sys in Ubuntu)

These are the drivers needed to run the Wifi card in Ubuntu.

3) Using the Ubuntu system install the ndiswrapper software, a full guide can be found here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I had the Edgy cd, so I inserted the live Ubuntu cd, clicked on System>>Administration>>synaptic Package Manager (you will be asked for your Superuser password, the one you log in with) Do a search for **ndiswrapper** choose the ndiswrapper-utils-1.8 (current version at time of writing); then right click and choose mark for installation. Then click **apply** at the top of the window. Ubuntu will install from the cd to your OS.

This software is needed to enable Ubuntu to run the windows wireless drivers in its Linux OS. (Genius when it works)

4)Open a terminal Applications>>Accessories>>Terminal then type:
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```
you will be asked for your superuser password again, just enter it. Unlike Windows it will not seem your passsword is being entered as the cursor doesn't move, don't worry it is ;) Close the terminal.

5) Insert your usb stick, with the drivers on them into the Ubuntu usb slot.
Create a directory in your 'home' area, I named mine **windows-drivers**.
Place the two bcmwl5 files into that directory, you will see the are named bcmwl5.inf and bcmwl5.sys now.

6)Open a terminal and type:
```
cd /windows-drivers
```
This will ensure you are in the correct directory. If you name the directory different to mine, just replace windows-drivers with the name of your directory. If at any time you need to check where you put the files, you can use the desktop (click places>>homefolder), or type **dir** in the command line, which will show all files/folders in that directory.

Once in the directory that contains the .inf and .sys files type the follwing in the command line:
```
sudo ndiswrapper -i bcmwl5.inf
```
this will make ndiswrapper copy these files into the correct location.
7) Now type 
```
ndiswrapper -l
```
If the driver is installed correctly you will see the following:
```
Installed ndis drivers:
bcmwl5 driver present 
```

8)In the terminal type the following
```
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper
```

To check the correct file has been created navigate to Places>>Computer>>Filesystem>>'/etc/modprobe.d/ there will be a file called 'ndiswrapper'. Double click on it and ensure the following line is present
```
alias wlan0 ndiswrapper
```
Alternatively in the terminal type 
```
gedit /etc/modprobe.d/ndiswrapper
``` This will get the same result, a text edit window (like notepad) with the 'alias wlan0 ndiswrapper code' displayed.
Then type
```
dmesg
```
in the terminal, a long list will be displayed, search for an entry which says 
> ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
ndiswrapper: driver bcmwl5 (Broadcom,06/25/2004, 3.40.73.0) loaded

Now close the terminal, remove the Ubuntu live cd, and shutdown the Ubuntu system. Unplug the power cable and wait a few minutes, then install the Buffalo wireless card (being careful of static).

Reboot the system, open a terminal and type
```
sudo ndiswrapper -l
``` (again you will be asked for your password)
You should see the following:
```
bcmwl5       driver installed, hardware present
```
This is important, it needs to appear just as above, otherwise ndiswrapper has not installed the driver properly.
Now type```
ifconfig
``` and you should see the output of the wireless card with an inet address, and a Bcast address, and a Mask address too.
Close the terminal and click System>>Administration>>Networking highlight the wireless connection and type in the network name, password type as 'plain' and configuration as 'Automatic Configuration (DHCP)'
Of course you must ensure your router is setup for 'Automatic COnfiguration (DHCP) also, you can retrieve the network name from your router also.Click on 'OK' and then check the small box nxt to the 'Wireless Connection'. Ubuntu will then attempt to start the connection. Once this is done, open a terminal and type
```
ping -c 4 192.168.0.1
``` where the IP address is that of your router. You should send/recieve 4 successful packets. Then type the following to reach the outside world:
```
ping -c 4 www.google.com
```
Again you should send successful pings, you are now connected (A big cheer went up, and drinks were poured when this happened ;) )

To ensure the drivers load successfully upon startup type the following:
```
sudo gedit /etc/modules
```
At the bottom ensure you type
**ndiswrapper** with a carriage return at the end. Close all windows and reboot. 
Fingers crossed all will be working, and you can connect to the outside world.

If the drivers are installed, yet you cannot connect to the router check Ubuntu is set-up to connect to the correct channel for your router (this can be found by accessing your router's setup page). Mine was 6 so I entered the following in the command line:
```
sudo iwconfig wlan0 channel 6
```
Then type
```
sudo iwlist wlan0 scan
```
You should get a scan result.

Resources and sources:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)
[http://ubuntuforums.org/showthread.php?t=272813](http://ubuntuforums.org/showthread.php?t=272813)

I must thank the authors of all the above links,especially the last, without this help I would have given up on an OS I have an increasing passion for. 
Of course this is on an open network, encryption is the next project.
A big thankyou to all the developers and members of this community, it is a great OS.
Best wishes :)

---

### Post by tylerdurden on 2007-02-05
thank u so much! ive been looking for this!

---

### Post by haz2a on 2007-02-07
Thanks for your excellent how-to. It would have taken me twice as long without your guide.

Your procedure works almost exactly the same for Ubuntu and Xubuntu 6.06 LTS with one slight modification: I had to do 'sudo ndiswrapper -m' after 'modprobe ndiswrapper' in step 8, to create the file /etc/modprobe.d/ndiswrapper.

---

### Post by GS2 on 2007-03-13
I'm glad it worked for you both :)

I think you may be right haz2a with the extra step -thank you for the input.

I will be updating my Ubuntu Edgy install to Feisty soon, so I will post if the method is still the same, and amend it if necessary.

It did not seem to work on Kubuntu Feisty, but I followed this guide that does not need ndiswrapper:

[http://ubuntuforums.org/showthread.php?t=185174&highlight=how+to+broadcom](http://ubuntuforums.org/showthread.php?t=185174&highlight=how+to+broadcom)

I used the same card, and the files for firmware I got from the link over at 
[ftp://ftp.dell.com/network/R81433.EXE](ftp://ftp.dell.com/network/R81433.EXE)
(I have saved a back up in case the link stops working)

thanks to the ndiswrapper list and to sourceforge :)

---

