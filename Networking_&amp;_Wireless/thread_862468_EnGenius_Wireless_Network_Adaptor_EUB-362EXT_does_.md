---
title: "EnGenius Wireless Network Adaptor EUB-362EXT does not work in Ubuntu Studio 8.04"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by TinusB on 2008-07-17
Hello!

The first time I moved a mouse on a computer running Linux was a few weeks ago when I installed Ubuntu on my new computer.
I bought an Ubuntu Studio 8.04 (Hardy Heron) Alternate DVD (amd64) 2.6.24-16-rt and it installed like a breeze on my Gigabyte computer with a GA-945GCM-S2C motherboard, Intel Pentium Dual Core 2GHz processor, 1GB RAM, 320GB harddisk (Windows XP Professional running on 137GB and Ubuntu on the rest), GeForce 8400 graphics card, LG DVD RAM, 17" Mecer C708 Monitor and the DVD ROM and Sound Blaster Live! 5.1 soundcard from an other computer.
The computer was runnig a perfect 1024X768 resolution when Ubuntu started up the first time and the sounds played absolutely right over the SBLive 5.1 - the card I wanted to work with.

But when I wanted to install my EnGenius (SENAO) WLAN USB 2.0 Wireless Network Adapter (EUB-362EXT 802.11b/g), hours of struggle came my way.
In the help section I read that I have to use Ndiswrapper, so I went to the internet and found this page: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I had to choose to install Ndiswrapper without internet connection, so I followed Step 2.2.1 on the page, downloading the 3 packages for 8.04 (amd64) and installed them in the right order. The installation was successful.
Then I had to blacklist some drivers as the page told me at step 3.1:

echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist

I did the same with ath_pci and ath_hal as they told me.

Then I followed the other steps to where I could note down the contents of the chipset ID (it was 0cf3:0002).

Now suddenly Rosegarden has no midi playback! The sounds appear to play, but there is no sound (yes, the JACK audio server is running). And that little sound at the login window does not play anymore, but the Ubuntu startup sound plays right.

Then came the step where I had to extract the driver files to get the .bin, .sys and .inf files.
After this time consuming battle I managed to extract the Windows XP driver that came with the modem and installed the inf file.
On the list on ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/ they said that it will work with the WinXP driver shipped with the product, but no way. I also downloaded the driver they suggested there. The ar5523.bin, ar5523.sys and net5523.inf was in the same folder on the harddisk. Same disappointing result.

When entering System>Administration>Windows Wireless Drivers (the Ndiswrapper driver installation tool) an error message comes up: Unable to see if hardware is present. When I click OK, net5523 shows on the list of Currently Installed Windows Drivers, as well as: Hardware present: Yes. When I unplug the modem and enter the tool again, it is: Hardware present: No. So something is happening, but I cannot configure the network in Configure Network. There is no wireless connection on the list.

In Terminal ndiswrapper -l gives:

WARNING: /etc/modprobe.d/blacklist line 40: ignoring bad line starting with '¨blacklist'
WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with '¨blacklist'
net5523 : driver installed
	device (0CF3:0002) present


This is the blacklist file:

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

¨blacklist bcm43xxnblacklist b43nblacklist b43legacynblacklist ssb¨
¨blacklist ath_pcinblacklist ath_hal¨


ifconfig displays:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2030 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2030 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:102220 (99.8 KB)  TX bytes:102220 (99.8 KB)


iwconfig displays:

lo        no wireless extensions.

eth0      no wireless extensions.


Any help will be highly appreciated.

---

### Post by TinusB on 2008-09-16
Can somebody please help me to reverse this process? How do I savely remove the 3 Ndiswrapper packages **and remove the lines from the blacklist**? I am going to try something else.

---

### Post by rgarcia on 2008-09-24
tried with this

1- sudo apt-cdrom add

2- install software "wireless windows driver" from application opcion add and remove

3- lsusb

4- sudo ndiswrapper -i name-driver.inf

5- sudo ndiswrapper -l

6- sudo ndiswrapper -ma

7- sudo modprobe ndiswrapper

8- sudo nano /etc/modules and write 
ndiswrapper

9-ifconfig and you see interface wlan0

10- sudo ifconfig wlan0 up

11- sudo iwlist scan and you see the wireless

11- sudo iwconfig wlan0 essid any

12- sudo iwconfig wlan0 essid "name wireless" 

13- sudo iwconfig wlan0 channel 11  put channel of you wireless

14- sudo iwconfig wlan0 key 5B4255B399545C18ED1CF3238F put your key in this case the wireless is encryted

15- sudo dhclient wlan0

16- ping google.com

17-navegate to internet

---

### Post by dommer on 2008-10-01
RGarcia, great writeup, but can I pose a second question to you:

If I'm using the external wireless as a second wireless connection and already have an internal wireless (I know, it's an odd situation, but the external one has much better range and sometimes I can't get a signal).  Is there a way to set up the second as wlan1?  The ndiswrapper -m command seems to want to use wlan0.

Thanks!

---

### Post by Manafo on 2008-10-06
bump !

---

### Post by rgarcia on 2008-10-23
Sorry for the long waiting 

In my case the wireless is extern with usb port and I have wireless internal and i don't have any problem.

---

### Post by TinusB on 2008-11-06
I have to admit that I chickened out with this (but not with Ubuntu!) and connected the Linux PC with a Windows XP PC with internet via a network cable (not an easy way either).
Thankyou very much for replying, RGarcia. As I see, this tread may give a solution for Dommer (and many others I hope).

---

