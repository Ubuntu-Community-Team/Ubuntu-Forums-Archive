---
title: "Total noob issues"
date: 2005-05-08
forum: Networking &amp; Wireless
---

### Post by MavisCruet on 2005-05-08
Hi, I have been trying to figure out how to get my ubuntu on line to read the forums so I can test it live, rather than rebooting to Windows.
I have been perusing the forums and FAQs but everything appears to be more complicated than I am up to yet.  I am a total linux noob (1st installed today).
I don't know if there is a simple way to install t'internet and I just don't know it or not.  Apologies for my total lack of knowledge.

I am trying to connect via a wireless router.  I have listed all (I think) the relevant kit below.

RT2500 usb wlan card
802.11g
128 wep
Intel 4 3.4ht
512mb ram
250SATA Hdd
Belkin router
NTL cable BB

Can someone offer advice or point me to an idiots guide?  I really don't know what I am doing yet, but want to learn.

---

### Post by dave9191 on 2005-05-08
Hey, try connecting to your router using the command line. Ill assume that you are using DHCP since you havent mentioned how you get your IP address. I find that it works best for me. type the following commands replacing the caps with your network details. And put the wep key in rather then a passphrase. (you may also have to use eth0 rather then eth1 depending on which one is your wireless card. iwconfig will tell you)

sudo iwconfig eth1 essid YOUR-NETWORK-ESSID
sudo iwconfig eth1 key YOUR-WEP-KEY
sudo iwconfig eth1 key restricted
sudo iwconfig eth1 ap YOUR-ACCESS-POINT-MAC-ADDRESS

Then type

iwconfig 

if it says unassociated next to your wirless interface then wait a little longer. Once it says IEEE 802.11 next to the ESSID, then you can request your IP using dhcp. 

dhclient

---

