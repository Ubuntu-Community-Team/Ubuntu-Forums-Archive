---
title: "no internet connection"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by jerrallan on 2006-10-17
I am still unable to connect to the internet on my wireless.  Have followed several threads and trouble shooting, but no luck.
The device is a Linksys WUSB54Gv4. ndiswrapper -l shows the hardware and driver is installed.
in System>Administration>Network shows wlan0 is active. Am using DHCP. Have entered ESSID and WEP Key asci.  I have also tried hex, but cannot get the computer to connect at all. no ping no nothing.
When i do sudo iwconfig I get:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"2WIRE864"
          Mode:Auto  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:XXXX-XXXX-XXXX-XXXX-XXXX  Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

I am grasping at straws right now.  I notice that the encryption key listed is a 20 digit number.  The number I listed during setup is a 10 digit number. Can anybody please point me in the right direction?  I am new to Linux, but I am learning.  Have tried about 5 different distros, and in spite of my problems, Ubuntu looks to be the best.
Help.

Thanks in advance
Okay, I found a work around. this  thread may be helpful to many but it did not help me:
[http://www.ubuntuforums.org/showthread.php?t=192588](http://www.ubuntuforums.org/showthread.php?t=192588)

I have to stick with rausb. But if I go to System>Administration>Networking and try to configure rausb, the screen will freeze. I have to reboot. So I don't activate it.*
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
1st addendum
I have installed my driver as per the above thread.  But I take the blacklist of rt2570 out of modprobe.d/blacklist.

In the terminal I enter:
sudo iwconfig rausb0 [myessid]
sudo iwconfig rausb0 encryption on    #this may not be necessary
sudo iwconfig rausb0 encryption [myencryptionnumber]
finally:
dhclient rausb0

I get an internet connection. But I have to do this everytime I reboot.  I finally made up a little script to semi-automate the process.
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
2nd addendum

*8/11/07-- I still am using my script [see above] to get an internet connection.  I have had no problems with it.  Why the computer freezes if I use System>Administration>Networking, I don't know.  Still using Ubuntu 6.06.

---

