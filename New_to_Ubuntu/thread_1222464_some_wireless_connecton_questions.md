---
title: "some wireless connecton questions"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by lsouth on 2009-07-24
Hello.  I have reinstalled with the ethernet cable attached so I got all the downloads I need I hope. 
some questions- 
What does VPN mean?
When I try to configure VPN, I get a network connections box. Under the wireless tab I find linksys, my wireless router.   What does "never" mean on the right end of the line linksys is on?  When I click ADD, I get an "Editing wireless connection 1" Box.
What is SSID?
In MODE, do I select infrastructure or as-hoc?
What is BSSID ?
What is MAC ADDRESS?
What is MTU ?  Do I leave it on Automatic?
As you can tell I know very little about this but I remember so I'll only ask once.
thanks
Lee

---

### Post by philcamlin on 2009-07-24
What does VPN mean?

vpn means virtual private network

What is SSID?

Service Set means all the devices associated with a specific local or enterprise 802.11 wireless LAN(s). ...

In MODE, do I select infrastructure or as-hoc?
infastructire

What is BSSID ?

Service Set means all the devices associated with a specific local or enterprise 802.11 wireless LAN(s). There are a few interrelated terms associated with service sets.

What is MAC ADDRESS?

In computer networking, a Media Access Control address (MAC address) is a unique identifier assigned to most network adapters or network interface ...

What is MTU ?  Do I leave it on Automatic?

In [computer networking]("http://en.wikipedia.org/wiki/Computer_networking"), the **maximum transmission unit (MTU)** of a layer of a [communications protocol]("http://en.wikipedia.org/wiki/Communications_protocol") is the size (in [bytes]("http://en.wikipedia.org/wiki/Byte")) of the largest [protocol data unit]("http://en.wikipedia.org/wiki/Protocol_data_unit") that it can pass onwards. MTU parameters usually appear in association with a communications interface ([NIC]("http://en.wikipedia.org/wiki/Network_interface_card"), [serial port]("http://en.wikipedia.org/wiki/Serial_port"), etc.). The MTU may be fixed by standards (as is the case with [Ethernet]("http://en.wikipedia.org/wiki/Ethernet")) or decided at connect time (as is usually the case with point-to-point serial links). A higher MTU brings greater efficiency because each packet carries more user data while protocol overheads,

yes leave it on automatic :popcorn:

---

### Post by lsouth on 2009-07-24
Thanks philcamlin, 
Now that they are defined, where do I go to learn the specifics of my equipment?  
I was connected to wireless briefly twice but it's off now.   I don't understand that but I must not have all the settings correct yet.
Thanks
Lee

---

### Post by mapes12 on 2009-07-25
> **lsouth said:**
> Thanks philcamlin, 
Now that they are defined, where do I go to learn the specifics of my equipment?  
I was connected to wireless briefly twice but it's off now.   I don't understand that but I must not have all the settings correct yet.
Thanks
Lee

Do you have a specific need for VPN? It's mainly used in Enterprise WAN's for secure internet connections to access corporate intranet and file server resources. If you are just looking for a secure world wide web internet connection then there should be no need to deploy VPN. If you are looking to connect to your wifi router via wifi on your laptop/desktop then in either case you will need to make sure that your wifi adapter on your laptop/desktop is supported in Linux. This could be why your connection has fallen over. As a first stage please could you post the output to ```
lspci
```

> where do I go to learn the specifics of my equipment? In Terminal ```
sudo lshw
``` is a good starting point.

---

### Post by 3rdalbum on 2009-07-25
The SSID is basically the name of the wireless network - it's what will appear as "your network" when you get a list of available wireless networks.

Under "mode", choose Infrastructure.

Don't worry about the other things, you don't need them.

---

