---
title: "[SOLVED] Tearing my hair out!"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by tropdoug on 2008-05-17
Hope someone can help me, before I go prematurely bald.

I have a laptop that was running perfectly with Ubuntu installed. I was having an issue with my wireless printer IP address changing and the puter was not picking it up. This led me too configure my router to use static IP addresses. I correctly put in the MAC and IP addresses of the printer, laptop and desktop and all seemed to be going alright. 

Then both the laptop and desktop were in use at the same time, and when we both tried to get on the net, the laptop stopped being able to access pages. When I investigated I found that the IP address in the router had changed to the same as the dektop. If I stopped using the net on the desktop the laptop would go ok. 

SO I decided that I had better revert to using dynamic DCHP and removed the static addreses. Thats good for the desktop, but now the laptop will not conect at all. (the desktop is wired)

In the network setup I have the wireless setup correctly, with the WPA and SSID entered properly. I have auto DHCP selected. 

The interface is coming up as [COLOR=Blue]eth1:avahi [COLOR=Black]but when I try to check the configuration it tells me that this interface does not exist. ??????

Eth0 and Eth1 are both not available? I can connect if I use a ethernet cable and activate the wired connection, which uses Eth1 but no more with the wireless. I have tried everything I can think of and am at my wits end. 

I am thinking I should uninstall all network devices and start again, but I don't know how to do that. I am still fairly new to Ubuntu.

Help wanted desperatly!! 
[/COLOR][/COLOR]

---

### Post by chili555 on 2008-05-17
> Eth0 and Eth1 are both not available? Nope. Please see here:[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

If you detach the cable, eth0, does the wireless work?

---

### Post by tropdoug on 2008-05-17
If I unplug the cable, wireless still doesn't work. It seems that this eth1:avahi is the problem, but I don't  know why it suddenly has appeared. I will check the docs out, thanks for the help so far

---

### Post by tropdoug on 2008-05-18
Ok got it solved, and it had nothing to do with Ubuntu. I am using a d-link DVA-G3340S Voip/ADSL/Router and somewhere in my fiddling I had reset the static IP addresses, which reluted in the registered client list becoming messed up. Once I went into the advanced tab, and then to LAN Clients I was able to re register the three IP's I needed and then ensure that each of the three hosts were configured with their correct IP addresses and all worked fine, so for other users of the DVA router make sure to check your LAN Clients addresses if things go a bit awry. 

Onto the next exciting issue. 

:-)

---

