---
title: "Can't get WUSB54G V4 active with Ndiswrapper"
date: 2006-12-22
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2006-12-22
Hello,

Installed...
Ubuntu Edgy 
Linksys WUSB54G V4 (*needs to connect to a WPA PSK wireless network & SSID hidden enabled) 
WPA supplicant
Ndiswrapper 1.8
WIndows RT2500 driver (*raus0 driver IS blacklisted)
Network Manager

 


Lights are on & the WUSB54G V4 is recognized....rt2500 & hardware...via the Windows Wireless Driver GUI. Good sign:D 

Networking shows NO wirreless, just my modem &  wired ethernet:( 

NetworkManager shows NO network connections:( 


etc/network/interfaces shows...

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0


   
I have been scouring the Wiki & forum entries, but cannot seem to get the adapter correctly configured. 

Would someone be willing to help a lost soul:???:

---

### Post by DapperMe17 on 2006-12-22
Anyone?

---

### Post by n00b@linux on 2006-12-22
Patience is a virtue ;)

To configure WPA the answer is staring you in the face: it's one of the stickies on this forum.   It's also the link in my sig.  

It presupposes you have the correct kernel module (ie. 'device driver') already loaded (or you've configured it with ndiswrapper).

---

### Post by DapperMe17 on 2006-12-22
Patience becoming thin with Linux wireless, my friend.

Latest kernel & correct Ralink driver installed, see above.

I have tried configuring according to the WPA link you have included...with no success. 

I've used synaptic to install the requirements, except for the Windows rt2500 driver. 


Do you have experience with the WUSB54G?

---

### Post by mjm115 on 2006-12-22
Have you tried [this thread]("http://www.ubuntuforums.org/showthread.php?t=192588")?

It deals specifically with your device in question.

---

### Post by DapperMe17 on 2006-12-22
Yes, I've looked at it. 

I used the gnome GUI tools to successfully add Ndiswrapper 1.8. WPA supplicant is installed.

The rtusb2500 driver was united with ndiswrapper via the gnome windows wireless drivers GUI tool.

The WUSB54G is recognized as a USB device, but does not appear to be configured correctly for WPA, per the interface config file. Network manager is not showing a wireless connection.

---

