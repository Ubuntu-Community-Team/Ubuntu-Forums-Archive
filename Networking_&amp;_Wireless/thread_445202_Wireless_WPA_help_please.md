---
title: "Wireless WPA help please"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by SirShaggy on 2007-05-15
I have been following this thread: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset) to set up my wireless card. I have a Belkin F5D7001 G+ card and it is working without WPA currently.

I am to the point where I need to enable WPA with Ndiswrapper driver. I just looked and my wireless device is called eth1 instaed of Wlan0 or Ath0. Now what? This has me confused.

I am supposed to ceate a file called /etc/wpa_supplicant.conf and input the following text:
ctrl_interface=/var/run/wpa_supplicant
 network={
   ssid="YourWiFiSSID"
   psk="YourWiFiPassword"
   key_mgmt=WPA-PSK
   proto=WPA
   pairwise=TKIP
 }

(of coarse using my SSID and PSK. I have tried it and get this response:

shaggy@shaggy-desktop:~$ sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 2 - start of a new network block
ssid - hexdump_ascii(len=10):
     53 68 61 67 67 79 41 74 68 30                     ShaggyAth0      
PSK (ASCII passphrase) - hexdump_ascii(len=41): [REMOVED]
key_mgmt: 0x2
proto: 0x1
pairwise: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line 8: removed CCMP from group cipher list since it was not allowed for pairwise cipher
Priority group 0
   id=0 ssid='ShaggyAth0'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'wlan0' UP
ioctl[SIOCGIWRANGE]: No such device
WEXT: Operstate: linkmode=1, operstate=5
ioctl[SIOCGIFINDEX]: No such device
Failed to add interface wlan0
State: DISCONNECTED -> DISCONNECTED
Segmentation fault (core dumped)
shaggy@shaggy-desktop:~$

As you see, it tries to check Wlan0, not eth1 like I have. Maybe this is simple for many but I hate this part and get lost easy. Any help appreciated.

SirShaggy

---

### Post by SirShaggy on 2007-05-15
Anybody? I really think at this point if someone can walk me through changing the name of my wireless connection from eth1 to wlan0, I can get through it. I just don't know what files need to be modified to make this happen.

SirShaggy

---

### Post by philmccaffrey on 2007-06-02
Hi I have the same problem... did you find a solution?

---

### Post by SirShaggy on 2007-06-04
> **philmccaffrey said:**
> Hi I have the same problem... did you find a solution?

No, not really. I have been working on it though. I ended up reinstalling Feisty to see if something just didn't work in the original install. I tried a few scripts and just haven't got it yet. I really suck with networking though! I mean, I can do almost anything but always fight networking. I have read about it in general, definitions and such, but really don't understand it. 

SirShaggy

PS - I will post back here when I do get it working properly......whenever that is.

---

### Post by kevdog on 2007-06-04
Couple of things -- ndiswrapper sets up everything my default to work on wlan0, but your system must have allocated like eth0 or something for your wireless interface.

There are three important files for you that you need to know about -  you can either change everything to eth0 or whatever interface you have that is working, or everything to wlan0.

To determine the current interface name assigned to your card, type ifconfig.  This should list a name associated with your wireless interface

Files
1. /etc/iftab -- This is actually the file that assigns the name to the network interface.  Edit this file with root privleges (sudo gedit) and change eth0 or whatever to wlan0
2. /etc/modprobe.d/ndiswrapper -- Again make sure that the interface name in this file is wlan0
3. /etc/network/interfaces -- Again you will rate to edit as root and change your current interface name to wlan0 (usually only two separate lines need to be edited.

Reboot the computer and you should be good to go!!!

---

### Post by dvyjones on 2007-06-06
I also have the same problem, I use Belkin F5d7001 card too, please tell me (us) if you have an answer...

---

### Post by TryMe on 2007-06-11
why not just change the command to

sudo wpa_supplicant -Dwext -ieth1 -c/etc/wpa_supplicant.conf -dd

---

