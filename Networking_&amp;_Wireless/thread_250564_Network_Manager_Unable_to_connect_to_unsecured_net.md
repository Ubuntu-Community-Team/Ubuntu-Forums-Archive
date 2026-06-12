---
title: "Network Manager Unable to connect to unsecured networks"
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by phyre-x on 2006-09-04
Hi, i've got a slight annoyance in that network manager will not connect to unsecured wireless network which i need to use at university , but i am only able to connect to my home wpa secured network with network manager, if i try to connect to an unsecured network with network manager the logo just keeps going round and round. 

i used network config tool in system menu to manually make my card (broadcom on ndiswrapper) connect to an unsecured wireless and it worked fine so im a little stumped as to why network manager will not as its functionality is something i was hoping for in dapper. 

also, the list of available network and hardware does not update very often, is there a way to change this and get my non-secured wireless accesible by the app ? 

thanks

---

### Post by wieman01 on 2006-09-04
Same frustrating experience here... I dropped NetworkManager after becoming fed up with its shortcomings such as lack of support for Static IPs, unsecured networks, hidden ESSIDs, and others.

I am afraid NetworkManager won't help unless they have enhanced the tool in the meantime.

---

### Post by phyre-x on 2006-09-04
frustrating as during my last installation prior to a different problem with network manager, i didnt have any problem connecting to unsecured networks. 

thanks - at least i know im not along lol

---

### Post by audioboxer217 on 2006-09-04
> **phyre-x said:**
> frustrating as during my last installation prior to a different problem with network manager, i didnt have any problem connecting to unsecured networks. 

thanks - at least i know im not along lol

I have a similar issue.  Network Manager was working on an unsecured wireless network, but then I had to do a reinstall and now it doesn't reconize my wirless card.

One thing that may be causing the problem is that I have the broadcom adapter that is set to eth1 (Ubuntu does reconize it as a wirless device and it does come up when I run iwconfig) but Network Manager says that I have no wireless devices. Again I say that it was working before I reinstalled.

---

### Post by phyre-x on 2006-09-04
have you commented out your wireless card from /etc/network/interfaces ? everything but local interface  and auto lo should be commented out i believe to let network manager take control.

let us know how it goes

---

### Post by Toady11 on 2006-09-11
same problem here - anyone have any luck fixing this?

---

