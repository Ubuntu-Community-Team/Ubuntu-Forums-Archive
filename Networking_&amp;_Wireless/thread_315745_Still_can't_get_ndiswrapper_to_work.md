---
title: "Still can't get ndiswrapper to work"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by glendavee on 2006-12-09
I've been fighting to get a working driver for  a Belkin USB wifi card which has the Broadcom4320 chipset. I have managed to install ndiswrapper-common 1.18-1ubuntu2 and ndiswrapper-utils-1.8 1.18-1ubuntu2, but when I attempt to install the driver from the windows CD(bcmrndis.inf) I get :
couldn't copy /home/david/drivers/bcmrndis.inf  at /usr/sbin/ndiswrapper-1.8 line 144
when I check installation with command ndiswrapper result is
Installed drivers  bcmrndis   invalid driver!
Can anyone tell me where I'm going wrong/ make helpful suggestions??

---

### Post by glendavee on 2006-12-11
Still can't get past this problem. Is there anybody out there??

---

### Post by FrodoB on 2006-12-11
Use sudo apt-get remove to get rid of the ndiswrapper that you installed and install the latest one. You will have to build it from source, here are the instructions. Once you get it installed you can remove and reinstall your driver.

Go to the ndiswrapper site and get the NDIS drivers that they recommend on other list.

Prepare the Linux build environment

You will need to install the essential build files to compile the driver:

user@ubuntu:~$ sudo apt-get update 
user@ubuntu:~$ sudo apt-get install build-essential

Install the correct headers for your version of Ubuntu: (don't worry if it tells you that yours are up to date.)

user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r` 
user@ubuntu:~$ sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build



Download the latest version of the ndiswrapper driver

Download the latest version of the ndiswrapper from sourceforge:

 [http://sourceforge.net/projects/ndiswrapper](http://sourceforge.net/projects/ndiswrapper)


It should be noted that as the ndiswrapper is further developed it could be the case that any particular NDIS driver compatibility could become broken for awhile.


Extract and install the ndiswrapper using make

Using tar extract the archived driver and change directories into the build area.

user@ubuntu:~$ tar xvzf ndiswrapper-1.31.tar.gz 
user@ubuntu:~$ cd ndiswrapper-1.31

Make the driver with the commands "make distclean", "make", and "make install":

user@ubuntu:~/ndiswrapper-1.31$ make distclean
user@ubuntu:~/ndiswrapper-1.31$ make
user@ubuntu:~/ndiswrapper-1.31$ sudo make install

The make process will take several minutes to complete.

You can now check the ndiswrapper to see that it is installed correctly. You should see something similar to:

user@ubuntu:~/ndiswrapper-1.31$ ndiswrapper -v
utils version: 1.9
driver version:        1.31
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1

Now go ahead and install your NDIS driver files as normal.

---

### Post by glendavee on 2006-12-11
Sorry if I appear thick. Two questions  - without internet access will I be able to get build-essential and all dependencies - will it be on installation CD?
Second, when installing headers, what is meant by 'uname-r' - do I use this exactly as is, or substitute something else relevant to the version of ubuntu I'm using (6.10)?

---

### Post by FrodoB on 2006-12-11
If you insert the install CD into a running system it will ask you if you want to open the package manager or something like that.  Click OK or yes and it will open synaptic.

type build and it should take you to it. Check it and the box will turn green then on the top tool bar click on Apply.

That should install what you need.

Then get ndiswrapper 1.31 download onto a USB drive or burn it to a CD for use in the Ubuntu machine from one that is networked.

cut and paste these commands:

user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r` 
user@ubuntu:~$ sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build

copy them into a text file and using a floppy or usb drive get the instruction on to Ubuntu.

Note the the ` are the backwards ones that are on the same key as ~, just under the Esc key.

---

### Post by roachk71 on 2006-12-11
Perhaps this will be more helpful:

You're probably using a version of NDISwrapper which doesn't yet support your wireless chipset. There is a solution most likely to work.

If you're new to this, don't let the procedure scare you away; it should still only take a few minutes.

First, open Synaptic and locate the server kernel and headers, then download and install them (if you're using the generic kernel, the system may behave strangely later.)

You'll also need to install build-essential.

Next, see the NDISwrapper source link in my signature; follow that link and download the latest version of the source (1.31). Now unpack the source. Remember the ndiswrapper directory it extracts to: you'll need this in a little bit.

After you have all this done, reboot (be sure to use the Escape key to select the server kernel from the menu.) You need to be running this kernel for the following steps.

Remember the NDISwrapper directory I just mentioned? Change to that directory in the terminal:

```
sudo -s -H {You need to be root for this}

ndiswrapper -e drivername  {the module format has changed since}

chdir [path to ndiswrapper directory]

make uninstall  {do this two or three times; use your up-arrow to use your command history}

make && make install  {If there are warnings, these can safely be ignored}

```

Now, it's time to install your wireless driver. As usual, simply use:
```
ndiswrapper -i drivername.INF
```

Next, there are a couple of bugs to work around:

```
gedit /etc/modules
```
and insert this line at the end:
```
ndiswrapper
```

Then:
```
gedit /etc/init.d/wireless-network.sh
```
and place this line in the file:
```
/etc/init.d/networking restart
```
then make it executable:
```
chmod +x /etc/init.d/wireless-network.sh
```

and Finally, create a symlink pointing to it:
```
ln -s /etc/init.d/wireless-network.sh /etc/rcS.d/S42wireless-network
```

Now reboot, and set the wlan0 interface up for your router using the Networking panel, and reboot.

NOTE: This only applies to WEP-protected networks; if you have WPA2 enabled (strongly recommended), you need to change your /etc/network/interfaces file to look something like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.132
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1 
dns-nameservers 192.168.1.1
wpa-driver wext
wpa-conf managed
wpa-ssid {your SSID}
wpa-ap-scan 1 { or 2 for hidden SSID }
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk {hex key here; please see the wpa-passphrase man page about this}

```

WPA-Passphrase takes two arguments: your router's SSID, and your plain-text WPA passphrase. Simply cut and paste those two from the terminal into this file, then reboot.

---

### Post by glendavee on 2006-12-11
I've followed Frodo B instructions and managed to get ndiswrapper -1.13 successfully installed. However the driver install still fails with the same message :
couldn't copy at /usr/sbin/ndiswrapper line 144
Is it an issue with the bcmrndis.inf file I got from the Belkin CD?

---

### Post by FrodoB on 2006-12-11
Go to the ndiswrapper list:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

Find cards that have your exact chipset, that have success reports and use the recommended drivers. Do not worry if they are not from the manufacturer of your device necessarily.  If they are fine, if not use them from the links supplied.

Getting ndiswrapper to work requires searching for the NDIS drivers from Windows that work with the wrapper and not all of them do.

---

### Post by alexjr on 2006-12-12
Does the driver have a corresponding sys file. Also, were do you have the inf file saved. Try saving it on the root and see if you get the same problem. Are you doing this in the root account?

---

### Post by glendavee on 2006-12-12
I seem to have got ndiswrapper working ok. I've installed the bcmwl5.inf driver successfully, but it won't hoop up with the card. I'm going to try bcmwl5a.inf, but so far haven't found anywhere to download it. Any suggestions??

---

### Post by FrodoB on 2006-12-12
Did you try the one on the CD again.  Remove and reinstall.

---

### Post by glendavee on 2006-12-12
Deleted and reloaded the files from the CD (bcmrndis.inf, rndismpk.sys, usb8023k.sys). Different result. At ndiswrapper -i command output was :
installing bcmrndis...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
when I then use ndiswrapper -l result is  :
bcmrndis Invalid driver!
Tried couple of times, same result.

---

### Post by FrodoB on 2006-12-12
What is the output of lspci?

lspci -v

---

### Post by glendavee on 2006-12-12
I'm not able to cut and paste the entire output but I can see no reference anywhere to the wireless device. However in Device Manger the Belkin wireless card is listed, but most properties are listed as unknown

---

### Post by FrodoB on 2006-12-12
I am sorry, this is USB:

lsusb

---

### Post by glendavee on 2006-12-12
lsusb output includes the line :

Bus 005 Device 004:ID 050d:7051 Belkin Components

---

### Post by FrodoB on 2006-12-12
Here is a link to the ndiswrapper site, this should work, I hope:

[http://ndiswrapper.sourceforge.net/m...dex.php/List#B]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B")

Your device is listed and they got the drivers from the Windows CD:

Card: Belkin F5D7051 (USB 2.0 Adaptor 802.11g 125Mbps)[LIST]
[*]Chipset: BCM4320
[*]usbid: 050d:7051
[*]Driver: Used hidden driver's from installation CD - bcrndis.inf - installation via commandline - configuration via controlcenter.
[*]Other: Tested on Mandriva 2006 Free - ndiswrapper 1.13
[*]Other2: Keyboard freezes on hotpluging.[/LIST]

---

### Post by alexjr on 2006-12-12
Does it still say that it has and invalid drive when you view you available drivers?

ndiswrapper -l

If it says that it is pressent have you tried assigning it to you divice?
You have to use the PCIID. Run

lspci -n

this will show you the numer it's in the XXXX:XXXX
when you have the number assign it to the device by running

ndiswrapper -e XXXX:XXXX bcmwl5 (XXXX:XXXX is the device PCIID)

then run 

ndiswrapper -l

to see if assign it to your device...

---

### Post by glendavee on 2006-12-13
Still nothing. I've deleted the drivers and reloaded current ones from Belkin site. I've tried both the XP and 2000 driver files, same result with both. When I ndiswrapper -i , I get the message
"forcing parameter IBSSGMode from 0 to 2" (repeated on two lines),
and the driver lists as invalid.
Tried alexjr suggestion. the lspci -n command produces a list without any numbers relevant to the wanted usbid 050d:7501

---

### Post by FrodoB on 2006-12-13
Are you using:

 bcrndis.inf

as recommended?

---

### Post by FrodoB on 2006-12-13
What is the output of

ndiswrapper -l

---

### Post by glendavee on 2006-12-13
file I'm using is bcmrndis.inf. File bcrndis.inf can't be found. I have assumed that the original entry contained a typo.
Files in downloaded folder are
bcmrndis.inf   rndismpk.sys    usb8023k.sys

---

### Post by FrodoB on 2006-12-13
Have you tried this one?

[http://www.belkin.com/support/download/downloaddetails.asp?download=1871&lang=1](http://www.belkin.com/support/download/downloaddetails.asp?download=1871&lang=1)

---

### Post by glendavee on 2006-12-13
ndiswrapper -l gives:

bcmrndis  invalid driver!

---

### Post by FrodoB on 2006-12-13
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

See item 32

---

### Post by glendavee on 2006-12-14
I've downloaded the drivers from the Belkin link you sent and replaced existing files with this download. End result is the same. Invalid driver!

---

### Post by FrodoB on 2006-12-14
The only thing that I can recommend at this point it to do a web search on Google, and perhaps drop down to ndiswrapper 1.28 and see if you get the same results, you probably will.

---

### Post by glendavee on 2006-12-15
Cracked it! Solution was to give up on my current usb dongle. I am now using a Belkin 9050 MIMO dongle which uses Airgo Networks chipset. Using ndiswrapper 1.31 I was able to install the driver (rt73.inf) which came with the installation CD, and then configure the network connection.
Thanks for the help:)

---

