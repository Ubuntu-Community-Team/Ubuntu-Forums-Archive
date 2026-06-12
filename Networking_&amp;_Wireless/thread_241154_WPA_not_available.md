---
title: "WPA not available"
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by UncleAelfrich on 2006-08-21
I have a TrendNet TEW-423PI wireless card. I did a normal install of Dapper Drake, and it recognized both my Ethernet connection (eth0) and my wireless card (wlan0). I can connect to the Internet via my ethernet connection.

However, when I go to System>Administration>Networking, while it recognizes the Trendnet Cart (based on TI acx111 chipset), WPA is not available.

I don't know if because the card shows up in Networking whether it works or not. I do know I don't have a WPA option, (which is what my wireless network security runs.) I checked, and WPAsupplicant says it is installed. I also ran lspci, and that command recognizes the wireless card.

I installed Network Manager, but it merely says that there is no network. I don't have a button that says to "add a new network".

MY QUESTION: What do I have to do to get WPA to work on this card?

I have read some conflicting information on these forums. So, I thought I would try to state my situation as clearly as possible and see if I could get a clear answer.

Thank you for your help.

---

### Post by Fass on 2006-08-21
WPA is unfortunately not available through the Gnome settings. Such is the state of Gnome weirdness...

... in any case, when you installed network-manager-gnome (or kde, or whatever its non-Gnome GUI is called), did you uncomment all the references to your wireless card in /etc/network/interfaces?

Also, are you broadcasting your SSID? Network Manager is not so good at seeing hidden SSIDs, even if it has connected to them before, meaning you will have to enter it manually.

---

### Post by UncleAelfrich on 2006-08-22
Thanks for your help. I re-installed ubuntu, and commented out the wlan0 referene in /etc/network/interfaces.

Then when I installed network manager, it gave me the option to create anew wireless network. However, when I got to the screen where it asks about security, WEP were the only optins available. I then reinstalled wpasupplicant, but still no option for WPA in network manager.

What next?

PS. A year ago I built a gentoo linux machine, but after the initial thrill of taking several days to compile a system, the thrill went away. I like Ubuntu because it sets up so easily. Please tell me that getting wireless to work in gentoo would be even more difficult.

---

### Post by UncleAelfrich on 2006-08-24
bump

---

### Post by gannic on 2006-08-26
I am in the same boat with my ACX111 chip PCI card. My current belief is that WPA is only possible if you use ndiswrapper. However results seem to be hit and miss. Its just bad luck for us. My broadcom card (laptop) was up and running with WPA in 2 mins.

---

### Post by briggella on 2006-08-29
I have managed to get wpa working with a Dlink G650 card (atheros chipset) but have yet to get on the network with it. It will authenticate and connect but disconnects after a while which I am still looking into and will post here shortly. I used the documentation here using CVS which gives the latest snapshots and everything in this tutorial worked as it says it should.

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

It is a bit involved and I hope to solve the final stages soon.

---

