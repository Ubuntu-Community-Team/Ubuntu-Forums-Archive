---
title: "connecting feisty to an ad hoc airport network"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by Deguatt on 2007-05-28
Ok!  I finnaly broke down and posted!  I've read just about everything to do with wireless networking on this message board, and in Ubunto books, etc... but I can't figure this out!  I am NO tech guru wither.

Here's my problem -I got a small home network -sharing a cable modem through my eMac's Airport card (running OS X).  Works great with no WEP encryption but once I started using WEP I can't get on with my Ubuntu machine. Why would this be a problem?  It sees the network but can not get online. 

 I spent a day figuring out the connection for my Dell Inspiron running XP -it sees the network and gets online fine.

My Ubuntu Feisty Machine looks like this:

Connection Properties: ath0
GENERAL
Conection
Name:  ath0
Status: Idle
Activity
Recieved: 0 packets (0.0b)
Sent:  0 packets (0.0b)
Signal Strength: 85%

SETINGS FOR INTERFACE ath0
Wieless Settings
Network name (ESSID):  LukeNet
Password Tyoe:  WEP key (hexadecimal)
Network Password:  **********  --(yes the password is correct)

Connection Settings
Configuration:  Automatic configuration (DHCP)
IP Address: (blank)
Subnet Mask:  (blank)
Gateway Address:  (blank)



iwconfig=
lo         no wireless extensions.
eth0    no wireless extensions.
wifi0    no wireless extensions.
ath0    IEEE 802.11g     ESSID: "LukeNet"   Nikname: ""
           Mode: Managed   Frequency: 2.417 GHz   Access Point:  Not-Associated
           Bit Rate: 1Mb/s   Tx-Power: 9 dBm   Sensitivity=0/3
           Retry:off   RTS  thr:off   Fragment thr:off
           Power Management:off
           Link Quality=47/94   Signal level =-52 dBm   Noise level= -99 Dbm
           Rx invalid nwid:61440   Rx invalid crypt:0   Rx invalid frag:0
           Tx  excessive retries:0   Invalid misc:0   Missed beacon:0



/etc/network/interfaces =

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface atho dhcp
wireless-essid LukeNet
wireless-key  **********  (this is the corect key)


Don't know exzclty what all that meanse but if any one could suggest any sollutions to my quandrie I'd greatly appreciate it!

THANKS--deguat

---

