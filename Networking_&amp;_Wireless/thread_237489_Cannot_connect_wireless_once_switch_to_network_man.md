---
title: "Cannot connect wireless once switch to network manager"
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by keltong on 2006-08-16
Hi,

I am a ubuntu newbie and just installed Dapper on my Omnibook 500. I used a WPC11v3 wireless card and have not problem detecting the card and setting up wireless connection to my WRT54G router.

As I want to use this at hotspots, I tried to setup the Network Manager to better manage my wireless connection.

However, once I setup Network Manager, I can't connect anymore. I even tried taking out any encryption and still cannot connect.

I've try 2 methods, first is to put a '#' infront of everything in /etc/network/interfaces except:

auto lo
iface lo inet loopback

Then I tried to reinstall ubuntu and use automatix to install network manager.

Both methods fail to connect to my wireless router, with encryption (WEP) or without.

Am I missing something? I really like ubuntu, but I need to solve this else I can't move forward.

Thanks.

Kelvin
__________________________________________
[http://www.justpapa.com/](http://www.justpapa.com/)
[http://www.kespeisland.com/](http://www.kespeisland.com/)
[http://www.easywineguide.com/](http://www.easywineguide.com/)

---

### Post by theh0g on 2006-08-17
Same problem. Anyone?

---

### Post by Or'Enn on 2006-08-17
Same here. I had to switch to network manager, because network-admin caused random freezes with linksys WUSB54G, but it got connected at least, and I could use internet, for a while.
Network Manager finds the wireless net, but can't connect with the key.

---

### Post by keltong on 2006-08-20
I am now using "Wifi-Radar" which can be found in the Synaptic Package Manager and it is working perfectly. I can now easily switch my wireless connection from home to office to hotspots. No more Network Manager for me and kudos to Wifi-Radar!

---

### Post by Mighty_Ferguson on 2006-08-21
> **keltong said:**
> I am now using "Wifi-Radar" which can be found in the Synaptic Package Manager and it is working perfectly. I can now easily switch my wireless connection from home to office to hotspots. No more Network Manager for me and kudos to Wifi-Radar!

keltong,
Are you using wifi-radar with WPA at all, or only WEP? If WPA, was there a guide or how-to article you followed to get it working? 

Thanks,
-Mighty

---

### Post by oldguy46 on 2006-08-23
> **keltong said:**
> I am now using "Wifi-Radar" which can be found in the Synaptic Package Manager and it is working perfectly. I can now easily switch my wireless connection from home to office to hotspots. No more Network Manager for me and kudos to Wifi-Radar!

did you take Network manager off?  
og46

---

