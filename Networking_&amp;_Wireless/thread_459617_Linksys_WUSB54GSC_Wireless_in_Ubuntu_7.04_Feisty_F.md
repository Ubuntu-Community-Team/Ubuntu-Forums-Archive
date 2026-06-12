---
title: "Linksys WUSB54GSC Wireless in Ubuntu 7.04 Feisty Fawn"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by rdon on 2007-05-30
I am brand new to Linux, and had no idea what I was getting into as I try to finally migrate 100% away from MS Windows.  I spent about two weeks trying to get my wireless adapter to work, and gleaned the following instructions from various locations.  I finally got it to work for me, and thought maybe this could help others that may be having similar difficulties.
  As I really don't understand how or why this worked, I'm not able to answer any questions you may have.


NOTE: Leave the Wireless adapter disconnected and do not plug in until Step 6.



   * Remove any remains of any past versions of ndiswrapper. If you've really mashed your system trying to get this to work, a complete reinstall is highly recommended, since ndiswrapper's pieces and configurations are probably scattered throughout your system. If you installed using apt-get, then run "apt-get remove ndiswrapper-utils". If you compiled ndiswrapper, and installed it, then open a terminal, go into the directory where you ran "make" in the first place, and run "sudo make uninstall". If you used Synaptic Package Manager, find ndiswrapper-utils in Synaptic, right click it, and click on "Mark for COMPLETE Removal". Basically, use the reverse of the method you used to install ndiswrapper in the first place.

    * I recommend that you download the latest ndiswrapper from ndiswrapper.sourceforge.net for Step 2.  I got this to work using version 1.38.

    * Do not plug in the device 'till I say to do so in the tutorial!

    * I assume you know how to use the terminal, and how to make and change directories, and how to copy files. If you don't, see this page: [http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal).

    * These instructions got my system running on Ubuntu Feisty Fawn 7.04.

    

Step 1 - Install the essentials

If you haven't compiled anything before using "make", then you'll probably need to run this command. Open the terminal and run:



sudo apt-get install cpp gcc build-essential linux-headers-$(uname -r)



Step 2 - Build ndiswrapper

Extract ndiswrapper from ndiswrapper.sourceforge.net.  Go into the ndiswrapper folder in the terminal, and run:



sudo make uninstall

make

sudo make install



To complete the task, and to tell the kernel to always load ndiswrapper at startup, run this command:



sudo ndiswrapper -m



Step 3 - Getting the drivers



The driver files needed are WUSB54GSC.inf, usb8023.sys and rndismp.sys.  Have the MS Windows 2000 or XP driver CD needed for the wireless hardware, or download from the Linksys site.  The .inf file is located in the 'Drivers' folder.  The .sys files will need to be stripped from the data1.cab and data2.cab files found under the 'Utilities' directory.   To do this, you need to get unshield.  Run:



sudo apt-get install unshield



In the terminal, change to the "Utilities' directory containing the .cab files and run;



unshield x data1.cab

unshield x data2.cab



You'll find the drivers in the "2Kdriver" directory.  Make a new directory where you will copy the .ini and .sys files:



mkdir  ~/MyDrivers



...and then copy the .ini and .sys files into the 'MyDrivers' directory.



Step 4 - Installing drivers

In the terminal, "cd" into 'MyDrivers' directory and run this command to install the drivers:



sudo ndiswrapper -i WUSB54GSC.inf



Then, copy the .sys files into the 'wusb54gsc' directory:



sudo cp usb8023.sys /etc/ndiswrapper/wusb54gsc/

sudo cp rndismp.sys /etc/ndiswrapper/wusb54gsc/



Now run:



ndiswrapper -l



The terminal should return something like:

wusb54gsc : driver installed



Now run:



sudo modprobe ndiswrapper



Step 5 - Getting WUSB54GSC to Work in Feisty:

Apparently Feisty has a feature that limits the power that goes to USB devices. This is all well and good to protect USB devices, except when a device wants more power then the kernel likes. From what I gather, the WUSB54GSC may be one of those devices.



This feature can be turned off. Run:



sudo nano -w /etc/udev/rules.d/99-custom.rules



A new blank file opens up. Type in the following text. Keep the text as one line - do not let it wrap over to the next line.



BUS=="usb", SYSFS{idProduct}=="0026", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"



Type Ctrl+O, the ENTER key, then Ctrl+X. You are now done!



What did we just do? Well, the system that tracks for new devices is called udev. This system has a set of rules under /etc/udev/rules.d/. What we did was add a rule that said "If this device's product is 0026, and the idVendor is 13b1, run this command". The command forces Linux to use configuration choice #1 (which so happens to be ndiswrapper) for this device. The variable $devpath marks where the device's folder is.



Step 6 - Configure the wireless.  

Plug in the adapter and wait for a few moments.  (at this point I may have rebooted, I don't remember)

Verify that the driver is installed and the adapter is recognized by the system.  Run:



ndiswrapper -l



The terminal should return:

wusb54gsc : driver installed

        device (13B1:0026) present



You have to know what the device name of your wireless interface is. Typically this is wlan0. Be sure the interface is turned on.  Run:



sudo ifconfig wlan0 up



Next we'll get a list of all the available access points using the iwlist command.  Run:



iwlist wlan0 scanning



You should see something similar to the following:



wlan0 Scan completed :

   Cell 01 - Address: XX:XX:XX:XX:XX:XX

     ESSID:"Larry"

     Mode:Master

     Frequency:2.462 GHz (Channel 11)

     Quality=3/94 Signal level=-92 dBm Noise level=-95 dBm

     Encryption key:off

     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s

     24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s

     12 Mb/s; 48 Mb/s

     Extra:bcn_int=100

   Cell 02 - Address: XX:XX:XX:XX:XX:XX

     ESSID:"MYACCESSPOINT"

     Mode:Master

     Frequency:2.452 GHz (Channel 9)

     Quality=45/94 Signal level=-50 dBm Noise level=-95 dBm

     Encryption key:on

     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s

     6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s

     36 Mb/s; 48 Mb/s; 54 Mb/s

     Extra:bcn_int=200

   Cell 03 - Address: XX:XX:XX:XX:XX:XX

     ESSID:"motorola"

     Mode:Master

     Frequency:2.462 GHz (Channel 11)

     Quality=4/94 Signal level=-91 dBm Noise level=-95 dBm

     Encryption key:on

     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s

     24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s

     12 Mb/s; 48 Mb/s

     Extra:bcn_int=100



The output shows a quite a detailed list of the surrounding access points. You probably know which one you want. Take note of the essid. We'll use that to associate with that access point.



sudo iwconfig wlan0 essid MYACCESSPOINT



If the access point has some sort of WEP or WPA encryption enabled, you'll need to enter the key. If not, you can skip this step.



sudo iwconfig wlan0 key 12345abcde



You should now have a connection to the access point. But before you start using the interweb, you'll need to get an IP address. Most access points have DHCP servers that make this part easy. Just run the DHCP client to ask for an address.



sudo dhclient



That should provide output similar to the following:

Internet Systems Consortium DHCP Client V3.0.4

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/eth0/00:10:dc:55:8a:81

Sending on   LPF/eth0/00:10:dc:55:8a:81

Listening on LPF/wlan0/00:18:f8:a8:28:5e

Sending on   LPF/wlan0/00:18:f8:a8:28:5e

Sending on   Socket/fallback

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7

DHCPOFFER from 192.168.1.1

DHCPREQUEST on wlan0 to 255.255.255.255 port 67

DHCPACK from 192.168.1.1

bound to 192.168.1.108 -- renewal in 41878 seconds.



Finally, let's check that everything is working. Ping an address.



user@ubuntu:~$ ping [www.google.com](www.google.com)



Good Luck!

_________________________________________________________________________________________________________

information sources bibliography:

[http://ubuntuforums.org/showthread.php?t=225206&highlight=wusb54gsc](http://ubuntuforums.org/showthread.php?t=225206&highlight=wusb54gsc)

[http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html](http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html)

---

### Post by Asian_Wannabe on 2007-07-31
Thank you so much! I managed to get connected to the internet :D

---

### Post by desmondo on 2007-10-14
Thanks for your excellent howto!

I had 1 problem because I was using the wrong driver version. I followed the instructions on this ndiswrapper page (under WUSB54GSC):

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/)

and got the WinXP .inf file from Linksys:

[http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1154470123093&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1154470123093&pagename=Linksys%2FCommon%2FVisitorWrapper)

and the .sys files from Belkin (strange, yes, but they use the same chipset):

[http://www.belkin.com/support/download/downloaddetails.asp?download=1871&lang=1](http://www.belkin.com/support/download/downloaddetails.asp?download=1871&lang=1)

Note that these sys files must be renamed to all lower case, and also note they are named slightly differently (they have a 'k' before the .sys).

Thanks again, and hope this helps others!

---

### Post by kevdog on 2007-10-14
Why do you need more power for the device??????

---

### Post by javaJake on 2007-10-14
> **kevdog said:**
> Why do you need more power for the device??????

Well, it turns out the device itself *says* it needs more power. It's almost like the kernel and device are having a little argument. Of course, the kernel will win and simply not give it the power it "needs", but that udev rule mentioned forces the kernel into submission. It does however disable a safety feature so that too much power may reach the device and damage it, but I'm not sure how likely this is.

---

### Post by Merk42 on 2007-11-17
Well I've been dual booting Ubuntu and Windows for a while now. However at my new place I needed to get a wireless nub (the WUSB54GSC) and I've tried to make sense of the stuff in this thread.  The closest I've gotten is 'installing' the ini file and copying over the two sys files.  However when I run ndiswraper l it says invalid driver.

I'd always heard Ubuntu's wireless support was bad, but I never had to experience it until just now.  I hope (but doubt) Wireless "just works" in Hardy.

---

### Post by jerikoescozoo on 2008-01-19
Are There any Flavors of Linux that automattically recognize the 
wusb54gsc without having to go through all of this?  I keep trying
but I keep getting headaches.

---

### Post by javaJake on 2008-01-21
Yes. In Feisty you no longer need to do this if you have an internet connection. For all distros, *unless you use ndiswrapper* you NEED internet access to start. Just the way things work right now, and you can blame Linksys, not Linux.

---

### Post by justsixspaces on 2008-06-05
Hey, thank you so much for you HOWTO. I appreciate the time and effort you put in to helping those of us in need.

That said, I still need your help =P.

Whenever I do "sudo ifconfig wlan0 up"

I get the following error message:

"wlan0: ERROR while getting interface flags: No such device"

despite the fact that when I do "ndiswrapper -l" I get:

wusb54gsc: driver installed
           device (13B1:0026) present



any ideas?

Thanks in advance!

EDIT: I am using the newest Ubuntu 8.04. Thanks again!


> **rdon said:**
> I am brand new to Linux, and had no idea what I was getting into as I try to finally migrate 100% away from MS Windows.  I spent about two weeks trying to get my wireless adapter to work, and gleaned the following instructions from various locations.  I finally got it to work for me, and thought maybe this could help others that may be having similar difficulties.
  As I really don't understand how or why this worked, I'm not able to answer any questions you may have.


NOTE: Leave the Wireless adapter disconnected and do not plug in until Step 6.



   * Remove any remains of any past versions of ndiswrapper. If you've really mashed your system trying to get this to work, a complete reinstall is highly recommended, since ndiswrapper's pieces and configurations are probably scattered throughout your system. If you installed using apt-get, then run "apt-get remove ndiswrapper-utils". If you compiled ndiswrapper, and installed it, then open a terminal, go into the directory where you ran "make" in the first place, and run "sudo make uninstall". If you used Synaptic Package Manager, find ndiswrapper-utils in Synaptic, right click it, and click on "Mark for COMPLETE Removal". Basically, use the reverse of the method you used to install ndiswrapper in the first place.

    * I recommend that you download the latest ndiswrapper from ndiswrapper.sourceforge.net for Step 2.  I got this to work using version 1.38.

    * Do not plug in the device 'till I say to do so in the tutorial!

    * I assume you know how to use the terminal, and how to make and change directories, and how to copy files. If you don't, see this page: [http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal).

    * These instructions got my system running on Ubuntu Feisty Fawn 7.04.

    

Step 1 - Install the essentials

If you haven't compiled anything before using "make", then you'll probably need to run this command. Open the terminal and run:



sudo apt-get install cpp gcc build-essential linux-headers-$(uname -r)



Step 2 - Build ndiswrapper

Extract ndiswrapper from ndiswrapper.sourceforge.net.  Go into the ndiswrapper folder in the terminal, and run:



sudo make uninstall

make

sudo make install



To complete the task, and to tell the kernel to always load ndiswrapper at startup, run this command:



sudo ndiswrapper -m



Step 3 - Getting the drivers



The driver files needed are WUSB54GSC.inf, usb8023.sys and rndismp.sys.  Have the MS Windows 2000 or XP driver CD needed for the wireless hardware, or download from the Linksys site.  The .inf file is located in the 'Drivers' folder.  The .sys files will need to be stripped from the data1.cab and data2.cab files found under the 'Utilities' directory.   To do this, you need to get unshield.  Run:



sudo apt-get install unshield



In the terminal, change to the "Utilities' directory containing the .cab files and run;



unshield x data1.cab

unshield x data2.cab



You'll find the drivers in the "2Kdriver" directory.  Make a new directory where you will copy the .ini and .sys files:



mkdir  ~/MyDrivers



...and then copy the .ini and .sys files into the 'MyDrivers' directory.



Step 4 - Installing drivers

In the terminal, "cd" into 'MyDrivers' directory and run this command to install the drivers:



sudo ndiswrapper -i WUSB54GSC.inf



Then, copy the .sys files into the 'wusb54gsc' directory:



sudo cp usb8023.sys /etc/ndiswrapper/wusb54gsc/

sudo cp rndismp.sys /etc/ndiswrapper/wusb54gsc/



Now run:



ndiswrapper -l



The terminal should return something like:

wusb54gsc : driver installed



Now run:



sudo modprobe ndiswrapper



Step 5 - Getting WUSB54GSC to Work in Feisty:

Apparently Feisty has a feature that limits the power that goes to USB devices. This is all well and good to protect USB devices, except when a device wants more power then the kernel likes. From what I gather, the WUSB54GSC may be one of those devices.



This feature can be turned off. Run:



sudo nano -w /etc/udev/rules.d/99-custom.rules



A new blank file opens up. Type in the following text. Keep the text as one line - do not let it wrap over to the next line.



BUS=="usb", SYSFS{idProduct}=="0026", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"



Type Ctrl+O, the ENTER key, then Ctrl+X. You are now done!



What did we just do? Well, the system that tracks for new devices is called udev. This system has a set of rules under /etc/udev/rules.d/. What we did was add a rule that said "If this device's product is 0026, and the idVendor is 13b1, run this command". The command forces Linux to use configuration choice #1 (which so happens to be ndiswrapper) for this device. The variable $devpath marks where the device's folder is.



Step 6 - Configure the wireless.  

Plug in the adapter and wait for a few moments.  (at this point I may have rebooted, I don't remember)

Verify that the driver is installed and the adapter is recognized by the system.  Run:



ndiswrapper -l



The terminal should return:

wusb54gsc : driver installed

        device (13B1:0026) present



You have to know what the device name of your wireless interface is. Typically this is wlan0. Be sure the interface is turned on.  Run:



sudo ifconfig wlan0 up



Next we'll get a list of all the available access points using the iwlist command.  Run:



iwlist wlan0 scanning



You should see something similar to the following:



wlan0 Scan completed :

   Cell 01 - Address: XX:XX:XX:XX:XX:XX

     ESSID:"Larry"

     Mode:Master

     Frequency:2.462 GHz (Channel 11)

     Quality=3/94 Signal level=-92 dBm Noise level=-95 dBm

     Encryption key:off

     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s

     24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s

     12 Mb/s; 48 Mb/s

     Extra:bcn_int=100

   Cell 02 - Address: XX:XX:XX:XX:XX:XX

     ESSID:"MYACCESSPOINT"

     Mode:Master

     Frequency:2.452 GHz (Channel 9)

     Quality=45/94 Signal level=-50 dBm Noise level=-95 dBm

     Encryption key:on

     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s

     6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s

     36 Mb/s; 48 Mb/s; 54 Mb/s

     Extra:bcn_int=200

   Cell 03 - Address: XX:XX:XX:XX:XX:XX

     ESSID:"motorola"

     Mode:Master

     Frequency:2.462 GHz (Channel 11)

     Quality=4/94 Signal level=-91 dBm Noise level=-95 dBm

     Encryption key:on

     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s

     24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s

     12 Mb/s; 48 Mb/s

     Extra:bcn_int=100



The output shows a quite a detailed list of the surrounding access points. You probably know which one you want. Take note of the essid. We'll use that to associate with that access point.



sudo iwconfig wlan0 essid MYACCESSPOINT



If the access point has some sort of WEP or WPA encryption enabled, you'll need to enter the key. If not, you can skip this step.



sudo iwconfig wlan0 key 12345abcde



You should now have a connection to the access point. But before you start using the interweb, you'll need to get an IP address. Most access points have DHCP servers that make this part easy. Just run the DHCP client to ask for an address.



sudo dhclient



That should provide output similar to the following:

Internet Systems Consortium DHCP Client V3.0.4

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/eth0/00:10:dc:55:8a:81

Sending on   LPF/eth0/00:10:dc:55:8a:81

Listening on LPF/wlan0/00:18:f8:a8:28:5e

Sending on   LPF/wlan0/00:18:f8:a8:28:5e

Sending on   Socket/fallback

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7

DHCPOFFER from 192.168.1.1

DHCPREQUEST on wlan0 to 255.255.255.255 port 67

DHCPACK from 192.168.1.1

bound to 192.168.1.108 -- renewal in 41878 seconds.



Finally, let's check that everything is working. Ping an address.



user@ubuntu:~$ ping [www.google.com](www.google.com)



Good Luck!

_________________________________________________________________________________________________________

information sources bibliography:

[http://ubuntuforums.org/showthread.php?t=225206&highlight=wusb54gsc](http://ubuntuforums.org/showthread.php?t=225206&highlight=wusb54gsc)

[http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html](http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html)

---

### Post by cardinals_fan on 2008-06-05
> **justsixspaces said:**
> Hey, thank you so much for you HOWTO. I appreciate the time and effort you put in to helping those of us in need.

That said, I still need your help =P.

Whenever I do "sudo ifconfig wlan0 up"

I get the following error message:

"wlan0: ERROR while getting interface flags: No such device"

despite the fact that when I do "ndiswrapper -l" I get:

wusb54gsc: driver installed
           device (13B1:0026) present



any ideas?

Thanks in advance!

EDIT: I am using the newest Ubuntu 8.04. Thanks again!
Try ```
sudo ifconfig
```  Look at the entries.  It might be called rausb0 or something else.  Once you have the name, enter ```
sudo ifconfig *name here* up
```

---

### Post by justsixspaces on 2008-06-05
Hey, thanks so much for the quick reply, but all I get is eth0 which is my ehternet, and "lo" which is a local loopback.

any other ideas?

the light on the adaptor isn't even blinking despite that I've followed the directions above exactly.

The only thing I did differently, was since I don't have the actual WUSB54GSC.inf drivers because I don't have the CD and can't find them online (even on the Linksys website), I installed the vista drivers to my system, found the driver, opened it in notepad, and copied and pasted everything in there into a new txt file and just saved it as WUSB54GSC.inf.

I'm not sure if that would cause the problem, and if so, I'll gladly reinstall the drivers if anyone knows where I can find the legitimate drivers.

I just don't know where to get them.

Anyway, thanks again for your help.


> **cardinals_fan said:**
> Try ```
sudo ifconfig
```  Look at the entries.  It might be called rausb0 or something else.  Once you have the name, enter ```
sudo ifconfig *name here* up
```

---

### Post by cardinals_fan on 2008-06-05
Linksys has the drivers at [http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859918606&packedargs=sku%3D1154470123093&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=1860657915B03&displaypage=download#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859918606&packedargs=sku%3D1154470123093&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=1860657915B03&displaypage=download#versiondetail)

---

### Post by dnpate on 2008-07-04
Using Ubuntu 8.04 I get the same results as "justsixpaces".  I have been over the procedure many times all end the same.  Any ideas?  Tx. 
david

---

### Post by dnpate on 2008-07-04
Has anyone gotten the Linksys WUSB54GSC device working in ubuntu 8.04?

---

### Post by desmondo on 2008-07-05
Mine's working, using the same drivers I downloaded when I got it working in Feisty (see post #3 in this thread), and using the same procedure.

> **dnpate said:**
> Has anyone gotten the Linksys WUSB54GSC device working in ubuntu 8.04?

---

### Post by redalert8352 on 2008-07-09
i've gotten everything right except for the installing drivers part
i just cant seem to understand it
can sombody explain it to me in more detail and what to do
i got to the part when i entered ndiswrapper -l and it said invalid driver 
any ideas why?
i think i messed up on the MyDrivers part 
am i suppost to create a folder saying MyDrivers on the desktop?
and where do i put the usb8023.sys file
and the rndismp.sys file

---

### Post by dnpate on 2008-07-12
I am still struggling to get the wusb54gsc working in 8.04, but just realized I am using a athlon 4850e with is 64 bit I think.  could this keep it from working?

---

### Post by alekals on 2008-07-22
Hi,
i have try this:

-- Download driver from [good driver for WUSB54GSC]("http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1154470123093&pagename=Linksys%2FCommon%2FVisitorWrapper")

-- Installed from command:
```
ndiswapper -i wusb54gsc.inf 
```

-- Type command:
```
ndiswapper -l
```
 
-- My Ubuntu respond:  "invalid driver"

-- ok download this [FileSysSupport]("http://www.belkin.com/support/download/downloaddetails.asp?lang_id=1&file_id=2411") and install on winxp (or try utils back post)

-- Type this
```
 cp USB8023K.SYS rndismp.sys /etc/ndiswapper/wusb54gsc 
```

-- Type command:
```
ndiswapper -l
```

-- My Ubuntu respond:
wusb54gsc : driver installed
        device (13B1:0026) present

-- ok good create file "/etc/udev/rules.d/99-custom.rules"  and put in this line:
```
 BUS=="usb", SYSFS{idProduct}=="0026", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'" 
```

-- VERY IMPORTANT reboot SYSTEM

-- Now system is up plug in my WUSB54GSC

-- My Ubuntu respond on dmesg:
```

Jul 22 19:13:26 Terra kernel: [  447.607074] usb 5-2: new high speed USB device using ehci_hcd and address 2
Jul 22 19:13:27 Terra kernel: [  447.759711] usb 5-2: configuration #1 chosen from 1 choice
Jul 22 19:13:27 Terra kernel: [  447.889384] usb 5-2: reset high speed USB device using ehci_hcd and address 2
Jul 22 19:13:27 Terra loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver wusb54gsc
Jul 22 19:13:27 Terra kernel: [  448.089564] usbcore: registered new interface driver cdc_ether
Jul 22 19:13:27 Terra kernel: [  448.096675] usbcore: registered new interface driver rndis_host

```
-- Type command:
```
ndiswapper -l
```

-- My Ubuntu respond:
wusb54gsc : driver installed
        device (13B1:0026) present


Last info:

ubuntu server 8.04 kernel Linux  2.6.24-19-server

ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-server/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-19-server SMP mod_unload 686

**iwconfig don't view interface wlan0**


help me please !!!
(sorry for long post and for my english) :):)


Alekals

---

### Post by alekals on 2008-07-23
This is best solution !!!!

[http://www.jooz.net/rndis/](http://www.jooz.net/rndis/)

---

