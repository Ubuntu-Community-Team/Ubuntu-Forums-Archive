---
title: "auto wpa2 configuration won't auto connect"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by deebee19701 on 2011-05-24
I configured my /etc/network/interfaces to have my installation boot up and auto configure my eth0 and wlan0 interface. well the eth0 interface comes up without a hitch, but the wlan0 will not auto connect to my access point. my question is:

1) how do I bypass the network manager application and just use the configuration file from within interfaces?
2) with network manager I have to enter in a keyring too allow access to the access point, how do I get rid of it or have it part of my configuration?


---------------- configuration file ----------------------

#############################
# to reset after any changes
# /etc/init.d/networking restart
#

auto lo
iface lo inet loopback

# primary LAN interface

auto eth0

iface eth0 inet static
address 192.168.100.2
netmask 255.255.255.0
network 192.168.100.0
broadcast 192.168.100.255
gateway 192.168.100.1

##############################
#
# wifi wpa2 personal config
#
auto wlan0

# specifies the interface if dynamic or static
iface wlan0 inet static

address 10.0.0.3
gateway 10.0.0.1
netmask 255.255.255.0

# Wifi driver
wpa-driver west
wpa-ssid some_string

# scan 1 = broadcast 2 = hidden
wpa-ap-scan 1

# RSN = wpa2 WPA = wpa version1
wpa-proto RSN

# CCMP = WPA2 TKIP = WPA version 1
wpa-pairwise CCMP 

# wpa-psk = personal/preshared key 
# wpa-eap = enterprise/username password
wpa-key-mgmt WPA-PSK

# use wpa_passphrase <SSID> <ASCII KEY> to convert
# the ascii passphrase to hex. use the output from the
# psk= line

wpa-psk SomeLongHexLine

---

### Post by grahammechanical on 2011-05-25
Please do not take me for an expert on this subject. I am using Network Manager to connect both by ethernet and wireless to the same modem/router. Network Manager remembers the WPA-PSK pass phrase to connect to the modem and it also has an option to connect automatically. It is doing this just fine for me.

Do you want to connect to one router/network by ethernet and also use wireless to connect to a different router/network? That would explain why the address and gateway for wlan0 is so different from the address and gateway of auto eth0. On my system they are very similar with just the final number being different.

I think that Network Manager should be able to control connections to more than one access point. I have not tried it but I am confident that if I wanted to I could get wireless access to an unsecured wireless network of a neighbor, whilst having wired connection to my own router.

The mystery for me would then be how to use ethernet for one form of connection (such as downloads) and wireless for another form of connection (such Internet access). At the moment everything is going through ethernet as it is the default.

I guess that I might need to change the mode of the wireless connection from Infrastructure mode to Ad-hoc mode. But it would only be a guess and not based on experience. At least this post will bring your request to the top of the pile. My good deed for the day.

Regards.

---

### Post by deebee19701 on 2011-05-25
well what I really want to accomplish here is to have my cheesy netbook work as a simple server for my  routing and switching lab.  I want to be able to reboot the machine without walking over to it to type in the keyring password to bring the wifi up. I was hoping to bypass NetworkManager all together but for it to give me the freedom of configuring the interface to a remote AP when Im travelling

---

