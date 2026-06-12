---
title: "Where are these ARP Requests coming from?"
date: 2017-02-13
forum: Networking &amp; Wireless
---

### Post by Dr Spliff on 2017-02-13
Just doing some routine monitoring of my network, I noticed something fishy that I haven't noticed in past tcpdumps / .pcap's.  

There are two devices sending ARP Requests to my router rather obnoxiously, about 20 times a minute, most often simultaneously.  Furthermore, I cannot figure out what these devices are, and attempting to ping the IP Address results in "Host Unreachable."  

28	24.172462	SamsungE_de:8b:72	Broadcast	ARP	60	Who has 192.168.1.1? Tell 192.168.1.5
37	27.853019	TctMobil_2b:29:de	Broadcast	ARP	60	Who has 192.168.1.1? Tell 192.168.1.17

According to some google research on the MAC Addresses, the Samsung may be a TV and the TCTMobile appears to be a Alcatel Mobile Phone. 
I have a Samsung display that I use as my monitor, but it is not a smart-tv and has no network capabilities or interfaces in it.  My spouse and I both have Apple iPhones and have never had an Alcatel / TCT Mobile device.

Can anyone explain where these requests are coming from?  I don't notice any traffic being used by either, just the constant hammering of ARP requests to my router.  Furthermore, the only two current active IP addresses on my network are my desktop and my printer. 

My first thought was maybe someone is running an ARP Cache Poisoning attack on me, but there is no evidence of a Man-In-The-Middle Attack being performed as the IPs lead to nowhere.

---

### Post by gdesilva on 2017-02-13
I presume you have already tried turning off wifi to see whether the ARP Requests will stop? Alternatively, I would check the list of active MAC addresses on the router - if these two are not yours it could be your neighbour's which might be a real concern. Also, worthwhile turning off wifi on your Apple devices, just to make sure! I would turn off all devices and then turn them on one at a time - not the smartest way but it is a lot easier to track down the issue this way specially given the fact that you are getting 20 or so ARP Requests per minute.

---

### Post by chili555 on 2017-02-13
I also suggest changing the WPA2-PSK password. Reboot the router and see if these devices appear in the client list and if the ARP requests stop.

---

