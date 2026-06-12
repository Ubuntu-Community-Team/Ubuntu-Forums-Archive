---
title: "belkin 7050 problem...any alternative?"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by AlexenderReez on 2007-04-02
i'm using feisty and belkin 7050 usb wireless adapter.....
reez@aLExeNdeRrEeZ:~$ lsusb
Bus 005 Device 003: ID 050d:705c Belkin Components 
Bus 005 Device 002: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 005 Device 001: ID 0000:0000  

it suppose to detect wlan connction but

i got this

reez@aLExeNdeRrEeZ:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:0 dBm   Sensitivity=0/3  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

it is really strange because my friend that use pci card Giga Bit Lan that use [FONT="Arial Black"][COLOR="Navy"]**ath0 **[/COLOR][/FONT]connection get connection 24hours per day while my wireless adapter only can detect there is wireless connection but i can't connect to it...

is there any way i change to use ath0 connection?
please explain what is going on...what is the difference between ath0 ,eth0,eth1...and wlan...what is the best?****

---

### Post by teaker1s on 2007-04-02
try this, it could be router and wireless not connecting correctly or it could be config problem-either way.

```
sudo apt-get install network-manager-gnome
```
now on your desktop panel you want to click system administration networking

it's important to make sure that devices show un-configured so network-manager-gnome can control them. Shutdown and remove Ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in Passphrase or network key

also as I understand it, a wireless adapter can be eth1 or it can be forced to use wlan by editing config files. ath0 I believe is atheros wireless

---

### Post by AlexenderReez on 2007-04-03
thax:)

---

