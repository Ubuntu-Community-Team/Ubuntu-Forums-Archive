---
title: "Setting up Hotspot Shield through Network Manager?"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by gkbli on 2011-06-27
SOLVED. I am editing this for anyone else wanting to set up Hotspot Shield through the Ubuntu Network Manager.

I wanted to set up a VPN for my netbook when I connect public hotspots.

I got Hotspot Shield to work through the terminal using _[this]("http://www.youtube.com/watch?v=Njp--ZOEUfA")_ youtube video. It works alright, but I wanted to set it up through the network manager instead.


How to set Hotspot Shield up through Network Manager:

1. Download the "network management framework (VPNC plugin)" package in synaptic
2. Now go to [http://hotspotshield.com/clientless/iphone/get_started.php]("http://hotspotshield.com/clientless/iphone/get_started.php") for the Hotspot Shield settings.
3. Configure a new VPN in Network Manager
4. Choose "Cisco Compatible VPN (vpnc)" from the dropdown list. 
5. How to fill out the window that pops up:

Server = Gateway
Account = User name under "Optional"
Password = User password
Group Name = Group name
Secret = Group password

Leave everything else as default.

6. Click save and now you can connect to Hotspot Shield through Network Manager!

---

### Post by cariboo on 2011-06-27
If all you are going to be doing is surfing the internet and checking email, the builtin firewall should be enough without having to go to all the extra effort of setting up third party programs. Open a terminal and type:

```
sudo ufw enable
```

You can run a port scan form another computer on your network, you'll see that there are no open ports.

If you use web mail, check to see if there is a https connection available.

---

### Post by Arnold Martin on 2011-12-10
2. Now go to [http://hotspotshield.com/clientless/iphone/get_started.php](http://hotspotshield.com/clientless/iphone/get_started.php) for the Hotspot Shield settings

[SIZE=4]404 Brother![/SIZE] Where is it?

---

