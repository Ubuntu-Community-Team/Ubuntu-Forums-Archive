---
title: "Wireless USB Adapter Help....."
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by Xomphos on 2007-02-13
Hi,
I am really interested in doing a dual-boot with Ubuntu 6.06.1 and Windows XP. I have done a dual-boot before and I have used recent versions of Ubuntu several times before within the last year or two. However, I have not stuck with it because after HOURS of research, I have still not been able to find out how to use my Dell TrueMobile 1180 Wireless USB adapter with Ubuntu. That is the ONLY thing that has been keeping me from regulary using any form of Linux. It has been several months though since I have tried this, mabey even half a year. Is there any way or tutorial to show the way to get my Dell TrueMobile 1180 Wireless USB adapter to work with Ubuntu?
Thanks! :D

---

### Post by Floppyjoe on 2007-02-13
This Url may help you:

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

Floppyjoe

---

### Post by Xomphos on 2007-02-13
Thanks!
Turns out my wireless card is finally supported! However, do I simply "plug and play" with it?
  	
Linux--wlan-ng 	newer version uses Broadcom chipset

It said those two things in a couple of the information boxes-does this mean anything?

Thank you very much for your help so far.

Xomphos.

---

### Post by Floppyjoe on 2007-02-13
Click on System/Administration/Synaptic Package Manager and search for linux-wlan-ng and download that driver to your system to see if that will activate your card. You may need to restart.

---

### Post by Xomphos on 2007-02-13
Thank you very much for your help. However, how would I access the download if I can't get on the internet in the first place? Thanks! :D

---

### Post by Floppyjoe on 2007-02-13
Can you connect with a network cable?

---

### Post by Xomphos on 2007-02-13
Ya, but the last time I did that, I switched monitors too and the resolution was screwed up or not supported or something.
Thanks! :D

---

### Post by Floppyjoe on 2007-02-13
It's also on the Ubuntu install CD. Click on system/Aministration/Synaptic Package Manager.
The click on Edit/Add CDROM. Then click reload. Then search for linux-wlan-ng.

---

### Post by Xomphos on 2007-02-13
Thanks a lot for your help on this! I now cant wait to get Ubuntu installed!


Thanks! :D

---

### Post by Xomphos on 2007-02-14
Great, I finished my dual-boot setup and installed that driver. However, I cannot access my wireless (WEP) network under Ubuntu 6.0.6.1. The wireless card is recognized (yea!) in the network manager thing, but when I enter the WEP key and apply it, it tries to connect for a few moments but doesn't. I occasionaly see the quick flash of the status light while doing stuff like this. How can I get it to connect successfully. 
Thank you for your help so far! :D

---

### Post by ittiam on 2007-02-15
u have to use something called wpa_supplicant to set up your encrypted key!

see,
 [http://www.ubuntuforums.org/showthread.php?t=263136](http://www.ubuntuforums.org/showthread.php?t=263136)

---

### Post by Floppyjoe on 2007-02-15
> **ittiam said:**
> u have to use something called wpa_supplicant to set up your encrypted key!

see,
 [http://www.ubuntuforums.org/showthread.php?t=263136](http://www.ubuntuforums.org/showthread.php?t=263136)

You don't need wpa supplicant for WEP only for WPA.
Are you using network-manager applet to connect?
If not then you need set up your /etc/network/interfaces file properly.

---

### Post by Xomphos on 2007-02-15
Well, I have been working on this for over an hour and I still haven't really gotten anywhere. However, here are a few screenshots I took to hopefully provide you with some more information that could hopefully solve this problem:

[IMG]http://img.photobucket.com/albums/v207/METALMARIO5/untitled3.png[/IMG]


[IMG]http://img.photobucket.com/albums/v207/METALMARIO5/untitled2.jpg[/IMG]

[IMG]http://img.photobucket.com/albums/v207/METALMARIO5/untitled.jpg[/IMG]

Also, here is some text from that document you told me to edit I found (I couldn't edit it because it said I need privledges although I am the admin):

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


iface wlan0 inet dhcp
wireless-essid blahblahblah
wireless-key s:blahblahblah

auto wlan0

---------------------------------------------

So, what should I do? My network uses a WEP key that just uses numbers. How can I connect to it? I have used the help documents and still can't figure it out.

Thanks for your help so far! :D

---

### Post by Floppyjoe on 2007-02-15
To edit that file type in the terminal:
```
sudo gedit /etc/network/interfaces
```
you probably need a couple of lines like:
```
wireless-channel 6
wireless-mode managed
```
Where you enter the channel of your router.

What did you use to edit/create those screen shots?

---

### Post by Xomphos on 2007-02-15
Well, I entered the code as you specified and I still cannot connect to the internet. 

This is what iwconfig spits out:

blah@blahblah:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11-b  ESSID:"blahblah"  Nickname:"blahblah"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:46:45:B0
          Bit Rate:11 Mb/s   Tx-Power:2346 dBm
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Link Quality=40/92  Signal level=-46 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

----------------------------------------

Here is also the edited interfaces file:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


auto wlan0
iface wlan0 inet dhcp
wireless-essid   blahblah
wireless-key     numberedkey
wireless-channel 6
wireless-mode    managed

----------------------------------------------------------

Also, on my router settings, does "Wireless Network Mode" have to do anything with 'wireless-mode'? It is currently set at "Mixed", but there are other options such as "Disable", "B-Only", or "G-Only". 

So, what can I do to get this to work? I think I am pretty close.

Also, you asked about how I took those screenshots-I used the screenshot application in Ubuntu 6.0.6.1 Dapper, and saved them to my FAT32 partition and then edited them in MS Paint.

Thank-you for your help so far, I really appreciate it! :D

---

### Post by Floppyjoe on 2007-02-15
What is the output of :
```
ifconfig
```
Does it show an ip address?

How did you post those pictures into your post? Did you have to save them to some web location first or can you insert pictures into posts directly from your file system?

---

### Post by Xomphos on 2007-02-15
Here is the output of ifconfig:

blah@blahblah:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:18:52:AD:77
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:167 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:12084 (11.8 KiB)  TX bytes:12084 (11.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:16:E9:58
          inet6 addr: fe80::290:4bff:fe16:e958/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:2448 (2.3 KiB)

--------------------------------

So, what do I do now?

Also, to post pictures, save them to a web host first (I used photobucket), then in the post creation thing, twoards the top of the message box there is a yellow icon with a couple of mountains and a moon. Click on it, and paste the url for your image you uploaded that the web host gives you.

Thanks again for your help so far! :D

---

### Post by Floppyjoe on 2007-02-15
Can you put wlan0 in the default gateway device part of System/Administration/Networking?
[IMG]http://img.photobucket.com/albums/v207/METALMARIO5/untitled.jpg[/IMG]
If you can also post the part of lspci that has a reference to network controller.

---

### Post by Xomphos on 2007-02-15
For some reason, it wouldn't allow me to set it as the default gateway device. I selected it, but once I clicked back into the network settings, it was blank again. Also, what is "lspci"?

Thanks! :D

---

### Post by Xomphos on 2007-02-15
bump

---

### Post by Floppyjoe on 2007-02-16
```
lspci
```
actually it should be:
```
lsusb
```
because you have a usb device.

Is a command to list the PCI hardware on your computer. I wanted to see if your network controller was Broadcom chipset. Just to make sure that the linux-wlan-ng was the right driver for your device.

I'm not sure why you are having difficulties connecting still. Everything looks ok from here.
What is the output of:
```
sudo dhclient wlan0
```
also you might like to try:
```
sudo iwlist wlan0 scan
```
to see if your interface can see your router.

---

### Post by Xomphos on 2007-02-16
Here is the output of the information you wanted:

> blah@blahblah:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 002: ID 413c:8100 Dell Computer Corp. TrueMobile 1180 802.11b Adapter
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
blah@blahblah:~$ sudo dhclient wlan0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:90:4b:16:e9:58
Sending on   LPF/wlan0/00:90:4b:16:e9:58
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
blah@blahblah:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:55:00:55:00:55
                    ESSID:"blahblah"
                    Mode:Master
                    Encryption key:on
                    Channel:6
                    Quality:34/92  Signal level:-46 dBm  Noise level:-80 dBm

As you see, it recognizes my wireless network. How can I get on it though? I really feel like I am really close to getting it to work.

Thank-you for your help! :D

---

### Post by Floppyjoe on 2007-02-16
> blah@blahblah:~$ sudo iwlist wlan0 scan
wlan0 Scan completed :
Cell 01 - Address: 00:55:00:55:00:55
ESSID:"blahblah"
Mode:Master
Encryption keyn
Channel:6
Quality:34/92 Signal level:-46 dBm Noise level:-80 dBm

I see that the mode of the router is master here.
Maybe changing /etc/network/interfaces where it says
```
wireless-mode managed
```
to
```
wireless-mode master
```
will fix the problem.
```
sudo gedit /etc/network/interfaces
```

After changing this file reboot the computer.

---

### Post by Xomphos on 2007-02-16
Wow. This thing just won't work for me no matter what I do. Here is my current interfaces file:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


auto wlan0
iface wlan0 inet dhcp
wireless-essid BLAHBlah
wireless-key randomnumbers
wireless-channel 6
wireless-mode    Master

I also went into the network-manager settings and changed the code since it is all numbers from hexidecimal to ASCI-II, but that didn't work, so I changed it back.
Is there any problem with my router? It is a WRTG54GSV4 (Linksys), the internet connection type is DHCP, DDNS service (I don't know what it is) is disabled, MAC address clone is disabled, operating mode is "Gateway", wireless SSID broadcast is enabled, the WEP key is 64 bits 10 Hex digits, wireless MAC filter is disabled, authentication type is auto, CTS protection mode is disabled, frame burst is enabled, beacon interval is 100, AP Isolation is off, UPnP is enabled, my router also has information for things such as subnet mask, default gateway, DNS 1 and 2, and the MTU.

What can I do to get it to work?

Thank-you very much for your help on this issue so far, I really appreciate you taking your time to help me with this. :D

---

### Post by Floppyjoe on 2007-02-16
You might try disabling encryption on the router to see if you can connect that way with:
```
sudo dhclient wlan0
```
you would also have to take the wep key out of the /etc/network/interfaces file.

I also found some information about this card on the ndiswrapper site:maybe it might be worth a try if nothing else works.
> Card: Dell TrueMobile 1180 802.11b Adapter

    * Other: Linux 2.6.15 i586 Fedora 5 on a HP Pavilion 6360 AMD K6
    * Other: ndiswrapper-1.24
    * Other: encryption mode used: WEP
    * usbid: 413c:8100
    * Driver: 1180 driver file is r51652 installed netdelus Win98 drivers. [http://support.dell.com](http://support.dell.com) search for r51652 or 1180 USB english a newer driver is available in r56450 on the dell website and will be tried after a kernel upgrade.
    * Install notes: ndiswrapper -i NETDELUS.INF only installs the inf file, the other files in the W98SYS directory extracted with unshield must be manually copied to /etc/ndiswrapper/netdelus. 

---

### Post by Xomphos on 2007-02-16
Cool, thanks, I will need to try that out (Ndiswrapper), but before I do, I have a question about it:
I am not that familiar with ndiswrapper, but I have heard of it. Is there a tutorial you could please point me to for using it? Also, do I have to delete a bunch of other settings I already entered before I use ndiswrapper?

Thanks! :D

---

### Post by Floppyjoe on 2007-02-16
I have provided a link to the sourceforge.net ndiswrapper wiki which may answer some of your questions.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)

You will not need to adjust your settings much. I think you will need to blacklist the native driver though.

---

### Post by Xomphos on 2007-02-21
Sweet, thanks a lot! Now, when I get time, I shall probably try this out. Thank you very much for getting me online with Ubuntu! I really appreciate it! :D

---

