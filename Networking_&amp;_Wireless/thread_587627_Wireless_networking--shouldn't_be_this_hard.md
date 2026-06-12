---
title: "Wireless networking--shouldn't be this hard"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by ukalumni on 2007-10-22
I have an old IBM T20 Thinkpad that was running the 5.x server edition of Ubuntu. I upgraded tonight to Gutsy Gibbon's server edition, and I can't get on my network.

My pcmcia card is a Dell Truemobile 1150. It is old as the hills, but it has been supported natively in linux for years. I have never had to use any of the ndis wrapper stuff with this card.

I'm running no encryption, and iwconfig shows that the card sees the network. I see my essid, I have a link quality of 21/92 where I'm currently sitting, and I have the MAC address of my router listed.

However, when I run

/etc/init.d/networking restart

I get the No DHCPOFFERS received  and "No working leases in persistent database -sleeping" messages.

Incidentally, when I tried to upgrade to the 6.x version of ubuntu, I had this exact same problem, and I just went back to the 5.x version. But I would like to get Gutsy Gibbon working if anyone can help.

I have restarted my router and windows machines on the network have no problem getting DHCP addresses, so I'm certain the problem is not in the router.

Again, I can see my network with the iwconfig command, but I cannot get a DHCP address.

I tried setting it to a static IP address, but I still can't get on my network. Suggestions?

---

### Post by dmizer on 2007-10-23
what is the output of:
```
sudo iwlist <adapter> scan
iwconfig
```

where <adapter> should be replaced with the adapter's designation (ex. wlan0, ath0, eth0)

if iwconfig does not show your router's mac address, you are not connected to your access point, and therefore will be unable to retrieve a dhcp address.

what's your chipset?  post the output of:
```
lspci
```

---

