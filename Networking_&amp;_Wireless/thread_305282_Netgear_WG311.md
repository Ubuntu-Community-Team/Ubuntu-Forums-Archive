---
title: "Netgear WG311"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2006-11-23
I have installed a Netgear WG311NA (*WG3113CAH019944)(Taiwan) PCI card. Unfortunately, it isn't being recognized as a hardware device attached to the motherboard.

Xubuntu Dapper 6.06 (fresh install to HD)
D-Link wireless router, running WPA PSK encryption

Xubuntu is recognizing other internet connection hardware...dial-up & wired ethernet, but absolutely no wireless.

lspci -n doesn't ID the Netgear card, thus, not recognized as hardware.

The Netgear card is seated firmly in the PCI slot & have tried other slots. 
Is it possible that my HP Pavilion doesn't support wireless PCI? 

I previously tried a Linksys WMP54G V4 card...it was also NOT recognized as a hardware device.

Would any of my router specific settings have any inpact...such as WPA, SSID broadcast, etc? I am able to access the router, as is, with Windows machine. 

Do I have to specifically work as "root" in Xubuntu to see the card...? Drawing straws here.


Any help with this hardware issue would be great!

---

### Post by DapperMe17 on 2006-11-24
Come o now...there's lot's of collective brainpower in this forum to let this one go unsolved:p!! 

Thanks

---

### Post by FrodoB on 2006-11-24
Publish the output of:

lspci 

for this card, that should lead to the correct drivers.

There are at least three different versions:

WG311 v1          Atheros, should work out of the box, not likely yours

WG311 v2          TI? This should work with Edgy, Not sure of this one, but not likely yours either.

WG311 v3          Marvell, you will need ndiswrapper

I am reading / interpreting this from:

[http://linux-wless.passys.nl/query_part.php?brandname=Netgear](http://linux-wless.passys.nl/query_part.php?brandname=Netgear)

If it is Marvell, can some ndiswrapper expert jump in here and help please?

---

### Post by DapperMe17 on 2006-11-24
The model is Netgear WG311NA (*WG3113CAH019944)(Taiwan)...I would assume based on the above info, that this is V3.

lspci doesn't identify a wireless PCI card. 

This is the second card that hasn't been ID'd as hardware (Linksys WMP54g V4 is the other). 

My MOB is a KESTRAL MOB P2B-VT MOB (made by ASUS for HP) with VIA Apollo 133 chipset....since all ather hardware is identified, except for wireless PCI, I've been told it may be a MOB driver issue...? All other hardware on the PC is identified thru lspci, just neither wireless cards. 

Thanks

---

### Post by FrodoB on 2006-11-24
I would assume that if it cannot ID with lspci that any drivers that you might install cannot see it either.

---

### Post by DapperMe17 on 2006-11-24
Right...weird issue...I can't explain it:neutral: 

Maybe it's best to just pick up a wireless USB adapter.

---

### Post by 713aggie on 2006-11-25
so i am new to linux, and like a few people here I have WG311v3 wireless card. Now I am extremely confused as to if it works with 6.10 or not? If so, how do I do it. I looked at sourceforge, ndiswapper info, and got confused with the coding. I downloaded the ndiswapper from sourceforge, but don't know what to do with it.:(   I know this has been covered many times, just having a hard time trying to find a thread that could help me out. any help is appreciated, thanks.

---

### Post by FrodoB on 2006-11-25
I am fairly sure that it is a marvell and it can be made to work.  Can you give us the output of:

lspci

so we can investigate carefully before we put you to work on ndiswrapper?

---

### Post by FrodoB on 2006-11-25
OK, after some further web searches it appear to be a Marvell, so here is how I got mine to work, and it works quite well I might add:

= TRENDnet TEW-421PC H/W:B1 PC Card Wireless Adapter using ndiswrapper Installation =

The TEW-421PC is a PC Card 802.11g wireless device that uses the Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03) chipset. 

For this example we assume that we are building the device in the user's home directory.

Note: I have only tested this using 128bit (104bit) WEP and ndiswrapper 1.29.

Reference should be make to the ndiswrapper wiki if any doubts exist:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

You should test that your device is applicable to this instruction using lspci:
```

user@ubuntu:~$ lspci

```Your output from lspci should contain a line very much like this:
```

0X:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

```This procedure has been tested one time. As soon as I get the chance I will be doing a complete reinstall for verification.

== Step 1 - Remove any existing copies of ndiswrapper that you may have ==

```

user@ubuntu:~$ ndiswrapper

```If you get an error stating that the program is not installed then proceed to the Step 2.


Here is how to remove a copy that was installed using apt-get:
```

user@ubuntu:~$ sudo apt-get remove ndiswrapper

```If you have an existing copy that you installed using make then change to the driver's directory and remove it using make:
```

user@ubuntu:~$ make uninstall

```Run ndiswrapper once more to make sure that you get the not installed error message:
```

user@ubuntu:~$ ndiswrapper

```== Step 2 - Disable any Competing Drivers ==
  
This section is here for completeness. There are no competing drivers at this time, but this hopefully will change in the future and there will someday be a native driver.

Edit the /etc/modprobe.d/blacklist file: 
```

user@ubuntu:~$ sudo gedit /etc/modprobe.d/blacklist

```To the end of the file add the competing driver as blacklisted:
```

# Added to disable the tew-421pc kernel driver as we are using ndiswrapper:
blacklist ???????

```Save the file. The blacklisted module will not be loaded from now on.

Check the contents of the /etc/iftab file and make sure that no other device has the wlan0 driver name reserved for it:
```

user@ubuntu:~$ cat /etc/iftab

```If there are any lines assigning the name wlan0 to a MAC identifier then either remove that line or comment it out with the "#" character.

== Step 3 - Prepare the Linux build environment ==

You will need to install the essential build files to compile the driver:
```

user@ubuntu:~$ sudo apt-get update 
user@ubuntu:~$ sudo apt-get install build-essential

```Install the correct headers for your version of Ubuntu: (don't worry if it tells you that yours are up to date.)
```

user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r` 
user@ubuntu:~$ sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build

```
== Step 4 - Download the latest version of the ndiswrapper driver ==

Download the latest version of the ndiswrapper from sourceforge:

[http://sourceforge.net/projects/ndiswrapper](http://sourceforge.net/projects/ndiswrapper)


At the time I originally wrote this the latest version was 1.29:

[http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.29.tar.gz?modtime=1164273927&big_mirror=0](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.29.tar.gz?modtime=1164273927&big_mirror=0)


It should be noted that as the ndiswrapper is further developed it could be the case that any particular NDIS driver compatibility could become broken for awhile.


== Step 5 - Extract and install the ndiswrapper using make ==

If you downloaded the driver to your Desktop then move it to your home directory. Open the middle menu called "Places" and select "Home Folder", copy the ndiswrapper-1.29.tar.gz file into it.

Using tar extract the archived driver and change directories into the build area.
```

user@ubuntu:~$ tar xvzf ndiswrapper-1.29.tar.gz 
user@ubuntu:~$ cd ndiswrapper-1.29

```
Make the driver with the commands "make distclean", "make", and "make install":
```

user@ubuntu:~/ndiswrapper-1.29$ make distclean
user@ubuntu:~/ndiswrapper-1.29$ make
user@ubuntu:~/ndiswrapper-1.29$ sudo make install

```The make process will take several minutes to complete.


You can now check the ndiswrapper to see that it is installed correctly. You should see something similar to:
```

user@ubuntu:~/ndiswrapper-1.29$ ndiswrapper -v
utils version: 1.9
driver version:        1.29
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1

```Obtain the Windows NDIS drivers that you intend to use with the device. In this case we are going to download the drivers from the TRENDnet site. For another device you should look at the ndiswrapper site's device listing and obtain your drivers from the described location. Or if you only have the install CD you can try to use those drivers, but they may not work.


The driver that we are using can be obtained from TRENDnet:

View download area:
[http://www.trendnet.com/asp/download_manager/list_subcategory.asp?SUBTYPE_ID=705#](http://www.trendnet.com/asp/download_manager/list_subcategory.asp?SUBTYPE_ID=705#)


Direct Link to driver:
[http://downloads.trendnet.com/TEW-421PC_b1%5CDriver%5CUtility_Driver_TEW-421PC_423PI_b1_2.00.zip](http://downloads.trendnet.com/TEW-421PC_b1%5CDriver%5CUtility_Driver_TEW-421PC_423PI_b1_2.00.zip)


Our driver file's name is either TEW-421PC_b1\Driver\Utility_Driver_TEW-421PC_423PI_b1_2.00.zip or Utility_Driver_TEW-421PC_423PI_b1_2.00.zip depending upon which link you download it from.


After Downloading the file it will probably be on your desktop. Open the middle menu called "Places" and select "Home Folder", create a directory called tew-421pc and put the file into it.

When we get an archive file from a manufacturer, the following tools may be required to extract the archive:
```

cabextract
unshield 
unzip

```In this case we are going to use unzip.

Extract the file using unzip: 
```

user@ubuntu:~/ndiswrapper-1.29$ cd ~ 
user@ubuntu:~$ cd tew-421pc
user@ubuntu:~/tew-421pc$ unzip TEW-421PC_b1\\Driver\\Utility_Driver_TEW-421PC_423PI_b1_2.00.zip 

```
Now we can change it to the Drivers/Windows XP directory and install the driver:
```

user@ubuntu:~/tew-421pc$ cd Drivers/Windows\ XP/
user@ubuntu:~/tew-421pc/Drivers/Windows XP$  sudo ndiswrapper -i Mrv8000c.INF 

```You should see output similar to this during the install:
```

installing mrv8000c ...

```You should not receive any warnings or errors.

Return to your home directory using a bare cd command:
```

user@ubuntu:~/tew-421pc/Drivers/Windows XP$ cd
user@ubuntu:~$

```Using ndiswrapper we can list the installed driver to make sure that we have it:
```

user@ubuntu:~$  ndiswrapper -l
installed drivers:
mrv8000c                driver installed, hardware (11AB:1FAA) present 

```If you device is plugged into the system you will see that the driver is installed and the hardware is present. If your device is not plugged in, then do so now and repeat this step to confirm hardware operation.


We can also look inside the directory where the drivers get stored by ndiswrapper:
```

user@ubuntu:~$  ls /etc/ndiswrapper
mrv8000c

```
And the contents of the mrv8000c subdirectory are:
```

user@ubuntu:~$  ls /etc/ndiswrapper/mrv8000c
11AB:1FAA.5.conf  mrv8000c.inf  mrv8000c.sys

```
Bring up the driver:
```

user@ubuntu:~$  sudo depmod -a
user@ubuntu:~$  sudo modprobe ndiswrapper

```If you do not get any errors and your system does not immediately freeze the driver should now be loaded. It may take a few seconds (12 - 30) for the modprobe to return, please wait. Do not reboot until we have made some basic checks and installed the driver permanently.


== Step 6 - Install the device and configure the network settings ==

Issuing an iwconfig command should reveal that your device is waiting to be configured, similar to this one:
```

user@ubuntu:~$  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          RTS thr:2432 B   Fragment thr:2432 B   
          Power Management:off
          Link Quality:95/100  Signal level:-35 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```You should be able to put your data in through the System-->Administration-->Networking applet. You just need to end up with the record formats that I am showing in my example. I used gedit to put the required record into the /etc/network/interfaces file: (note that the Xs are your actual WEP key.)
```

user@ubuntu:~$  sudo gedit /etc/network/interfaces

```Create a record that looks like this: (Note we are using 128bit WEP encryption in this example.)
```

iface wlan0 inet dhcp
wireless-essid My_Essid
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX
auto wlan0

```Save the file.

Make the driver permanent using the ndiswrapper method:
```

user@ubuntu:~$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
couldn't add module alias:  at /usr/sbin/ndiswrapper line 717.
user@ubuntu:~$ 

```Critical Notice: Check the file /etc/modprobe.d/ndiswrapper file and make sure that the ndiswrapper alias is wlan0 an not something else such as eth1.

Use cat to look at /etc/modprobe.d/ndiswrapper and ensure that it contains the line "alias wlan0 ndiswrapper" and nothing else:
```

user@ubuntu:~$ cat /etc/modprobe.d/ndiswrapper

```Make sure that it contains only the wlan0 identifier and no other:

alias wlan0 ndiswrapper


If it contains anything else edit /etc/modprobe.d/ndiswrapper and ensure that it contains the line "alias wlan0 ndiswrapper" and nothing else:
```

user@ubuntu:~$ sudo gedit /etc/modprobe.d/ndiswrapper

```Save the file.

Reboot your system in preparation for testing and validation of your work.

== Step 7 - Testing the device ==

Now when we run iwconfig we should see that your ESSID and Access Point fields have been filled in with your
access point's correct information and the Frequency field shows the correctly detected frequency:
```

user@ubuntu:~$  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"My_Essid"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:08:74:02:01:FC   
          Bit Rate:11 Mb/s   
          RTS thr:2432 B   Fragment thr:2432 B   
          Power Management:off
          Link Quality:95/100  Signal level:-35 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```The ESSID field should contain the name of your wireless network and the Access Point field should be filled in with the MAC identifier of your access point.

Run a "netstat -rn" command, and you should see that the correct routing is setup:
```

user@ubuntu:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.0.2     0.0.0.0         UG        0 0          0 wlan0
user@ubuntu:~$ 

```In this case 192.168.0.2 is the gateway address to an Internet router.

If everthing looks good then all of your network data has been entered correctly.

== Step 8 - Controlling the device ==

My system does not restart this device on startup, so I use the ifup and ifdown commands to control it. Scanning is supported in iwlist so you can scan for networks and wifi-radar works as well.

You can now control the device with ifup and ifdown:
```

user@ubuntu:~$ sudo ifdown wlan0
user@ubuntu:~$ sudo ifup wlan0
user@ubuntu:~$ sudo iwlist wlan0 scanning

```Removing and inserting the device should remove and setup the network correctly, at least it does with this device.

If you need to restore or change your system's route to the internet you can use dhclient:
```

user@ubuntu:~$ sudo dhclient wlan0

```Hopefully, you have arrived at the end of this procedure with a working device. Refer questions 
to the Networking & Wireless section of the forums.

---

### Post by FrodoB on 2006-11-25
Also note this post where the user tells you where he got the working drivers. These are the drivers you want to use then.

[http://www.linuxquestions.org/questions/showthread.php?t=400257](http://www.linuxquestions.org/questions/showthread.php?t=400257)

---

