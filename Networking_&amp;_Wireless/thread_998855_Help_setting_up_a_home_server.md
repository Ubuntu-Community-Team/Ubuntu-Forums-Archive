---
title: "Help setting up a home server"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by steviefordi on 2008-12-01
I have been using ubuntu for a few months now on my ageing desktop PC. In the new year I want to buy a laptop (on which I will install ubuntu) and use the desktop as a server. The laptop will be a client to the server.

I want the server to perform a few tasks:

[LIST=1]
[*]It will have a big hard drive for home directories and general data storage.
[*]It will have a printer connected to it for printing from the laptop.
[*]Internet access will be gained through the cable modem that's connected to the server via an ethernet card.
[*]Email Mail boxes are to be stored on the server
[*]Connectivity to the server will be through a wireless network cards (both on the server and laptop).
[*]I also need a backup solution (not sure what is best) to keep all the data backed up.
[/LIST]
Also, as the hardware on the server is quite old, I would like to minimise what runs on it (like no X window system if possible). Applications launched on the laptop are to run on the laptop, and the server's purpose will be storage, printing, backup and as a route to the internet.

My problem is I have no idea where to start. Any advice or links to guides and information would be greatly appreciated.

Thanks
Steve.

---

### Post by zotkop on 2008-12-01
First of all, I'd put a wifi-router between your cable connection and the server.
That way, you can give your server a static IP, and map your folders on the laptop.
Having the laptop sync with the server over wifi, and have the server connected to the www over ethernet sounds quite hard to me.

You might considder using the rsync command in your crontab to sync folders between the server and the laptop.

I'd keep the purpose of the server to a Samba (file & printersharing), and have the routing done by an external router. It will cost you a little bit more than the wireless dongle, but will save you lots of time.

This might be of interest:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

