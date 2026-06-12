---
title: "cannot change mac address"
date: 2014-07-08
forum: Networking &amp; Wireless
---

### Post by Apagon on 2014-07-08
xubuntu 13.10 and 14.04

I use wifi to connect to internet. I would like to change the wifi card mac address before connecting. Let's call the original mac address macA, and the new mac address macB. 
I do the following: 

[B][I]ifconfig wlan0 down && ifconfig wlan0 hw ether <macB> && ifconfig wlan0 up 
[/I][/B](I have also tried thiswith*** ip link set wlan0 address <macB>*** )

I check the new mac out: 
***ifconfig wlan0 | grep HW ***
It works: macB appears 

But then when I connect to internet, this is macA which is taken into account (I can see it when editing connection in Network Manager) (tcpdump should confirm this but havent tried)

So I disconnect, I erase all connections in Network manager, I disable networking, I set up macB (as done previously), but the issue remains when re-connecting

Actually, I could figure out the system behaves like this: 
when I change from macA to macB without connecting to internet, the system keeps macB (***watch -n 1 'ifconfig wlan0 | grep HW'***)
as soon as I try to connect to internet, the system gets back to macA instantaneously!! (so what's the point to change the mac this way ? :confused:)

does the wifi spot refuse the mac and have the client recheck its mac, does the client itself do a check of the mac address before connection? (yes I know I should read the corresponding rfc, but somebody may know)

I tried to install macchanger ([https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses](https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses)) but the package is unknown on my system. Actually I do not know how to include universe packages. 

Furthermore, as explain in [https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses](https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses), using macchanger, you cannot control the  vendor part of the mac address (which removes some privacy because it makes your mac "be quite conspicuous.". Instead doing it manually, you can control the vendor part, and put whatever you want in the rest of the address ....

thanx for your help folks !

---

### Post by Apagon on 2014-07-09
I finally included universe repositories and installed macchanger. 
guess what??? 

we have the exact same problem
- I put down wlan0, change the mac with macchanger
- as long as I stay without connecting to internet, the new mac stays in place 
- as soon as I try to connect, the system gets back to  the original mac.

---

### Post by Apagon on 2014-07-12
I could finally make it; it looks like the network manager does not stop correctly from gui. So doing (as root) :
**service network-manager stop && ifconfig wlan0 down && macchanger -A && ifconfig wlan0 up && service network-manager start && watch -n 1 'ifconfig wlan0 | grep HW'**

then you connect to a wifi spot and the new mac should stay in place.

using ***ifconfig wlan0 hw ether <fake_mac>*** or*** ip link set wlan0 address <fake_mac>*** instead of using macchanger works as well

thanx for reading guys.

---

