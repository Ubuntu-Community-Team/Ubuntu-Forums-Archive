---
title: "Wireless Help"
date: 2005-08-09
forum: Networking &amp; Wireless
---

### Post by ux5b2 on 2005-08-09
Hello.

When I first installed Ubuntu I ran into some problems with the standard gnome network app when trying to connect to wireless networks.  I created a simple script to help me connect to a wireless SSID of my choice which displays all the available networks and then connect to the SSID I choose (using iwconfig and ifup). 

This worked fine until now (connecting to my school network and public access points).  Now I need to be able to connect to my own network which has more security.  The problem is first that I want to be able to connect to a network where DHCP is disabled and also be able to connect to a network with encryption turned on (either WEP or WPA).  So basically I am asking first for the command to specify an IP address or DNS information (im not sure exactly what information is needed when DHCP is disabled)  in order to connect to a network without DHCP and also how to specify an encryption key (and possibly have it  stored for a given ssid so that I dont have to enter it every time I connect).  Any help is greaty appreciated.  Thank you for your time.

---

### Post by PeP on 2005-08-09
you will enjoy whereami, 
it can autodetect where you are and configure almost anything. you can also force it to a location (thus enabling the net config that suits to this location)
for example it can detect that there is an ap whose essid is "myownsecurewifi" in range and know that this wifi is at home then it is easy to configure:

=home ifconfig wlan0 192.168.1.123 netmask 255.255.255.0 broadcast 192.168.1.255
=home iwconfig essid "myownsecurewifi" key "WEPKEYBDhJCB" enc on
=home route add default gw 192.168.1.1
=home setresolver search mydomain nameserver 192.168.1.12

it also provides commands to change proxy settings, mail route ...



You might prefer a solution based on waproamd,ifplugd,guessnet and discover, I know a howto but it is in french:

[http://linuxfr.org/~artefact/16564.html](http://linuxfr.org/~artefact/16564.html)

you can also enhance your scripts to set up the wireless net :
add this kind of lines to your script
for encrypted wifi
iwconfig wlan0 essid "mysecurewifi" key "WEPKEYBDhJCB" enc on
no more encrypted:
iwconfig wlan0 enc off
static ip:
ifconfig wlan0 192.168.1.123 netmask 255.255.255.0 broadcast 192.168.0.255
gateway:
route add default gw 192.168.1.1

---

