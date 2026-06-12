---
title: "Trouble wirh wireless bitrate"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by MrHyde on 2007-11-05
Hi,

I think I am having some problems with bitrate on my wireless card.  I am using only the command line to set up the wireless connection and it connects ok, but is very very slow.  I havea  802.11g router and my Windows laptop connects to it using 54Mbps.  I can transfer a 200MB file between two windows machines in about 7 minutes.  Transferring the same file between Windows and the Ubuntu machine takes over 2 hours.

I have a wireless card using the RaLink RT2500 chipset.  I am using the built in drivers that come with Ubuntu Gutsy Gibbon.

[PHP]
vivek@supermachine:~$ sudo lspci | grep Network
02:06.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
[/PHP]

The following is my iwconfig output.
[PHP]
wlan0     IEEE 802.11g  ESSID:"Mittal"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0D:88:B8:D8:4C
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Encryption key:9876-5123-4098-7651-2340-1234-56
          Link Signal level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/PHP]

Notice that it does not mention what the current bitrate is.

The entries in /etc/network/interfaces is as follows:

[PHP]
auto wlan0
iface wlan0 inet dhcp
wireless-essid Mittal
wireless-key FEFEFEFEFEFEFEFEFEFEF
wireless-channel 1
wireless-mode managed
wireless-rate 54M
[/PHP]

When I run the iwlist wlan0 rate command, I get the following:
[PHP]
vivek@supermachine:~$ sudo iwlist wlan0 rate
wlan0     unknown bit-rate information.
[/PHP]

When I try to set the rate using the iwconfig command, I get
[PHP]
vivek@supermachine:~$ sudo iwconfig wlan0 rate 54M auto
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device wlan0 ; Operation not supported.
[/PHP]


Any ideas on how to proceed further.  I would prefer not to install ndiswrapper as it seems just too much of a hassle to get working properly.  Atleast, at the moment, my wireless does work, although not very useable.

Thank you 
Vivek

---

### Post by kevdog on 2007-11-05
You might want to explore using iwpriv rather than iwconfig.  iwpriv are private statements for the specific card driver.  I went to the serial monkey website to find the private iwpriv commands but I cant find them documented specifically.  Maybe the serialmonkey forums are a better place to ask.

---

### Post by MrHyde on 2007-11-06
iwpriv seems to be used only to set WPA parameters.  For everything else, I should be using iwconfig.

---

### Post by kevdog on 2007-11-06
Thats what the website states for iwpriv, but they do not publish all the iwpriv statements that are available.  iwpriv are "private" commands for the driver.  It would seem (all though I cant find them) that there should be a list of iwpriv commands for the driver.  I know iwpriv can be used for more than wpa parameters.

---

