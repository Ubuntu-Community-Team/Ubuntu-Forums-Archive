---
title: "Torrent works Web doesn't!?"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by BKK on 2007-08-01
Yesterday everything works well. I have not made any changes except firefox updated itself! When I use Ktorrent it works fine, file come down nice a quick. When I go to check any website nothing comes back! I have made sure the /etc/resolve.conf nameserver is the same as the windoze boxes...not sure where to look next...

---

### Post by PaulFr on 2007-08-01
I'd start with the following:
> 1. Run **sudo apt-get update** in a terminal to make sure everything is up-to-date.
2. Run **host [www.yahoo.com](www.yahoo.com)** or **dig [www.yahoo.com](www.yahoo.com)** to verify DNS resolution is working.
3. Run **ping [www.yahoo.com](www.yahoo.com)** to check your network path to [www.yahoo.com](www.yahoo.com) exists.
4. Start Firefox with a new profile by running **firefox -ProfileManager** and create a brand new profile with no add-ons and try to browse to [www.yahoo.com](www.yahoo.com). See if you get any error messages in the terminal.

---

### Post by BKK on 2007-08-03
Thanks, I did all of that. I had it working for a while. Now I can not get the wireless to connect at all. It asks me for the password and it seems like it times out. I went into the network manager to configure the connection. It doesn't work. We made some changes to the network. I am having this trouble at school. It is a small school here in Thailand. We changed computers in the lab to work on DHCP. These computers are all linked by wired network to the main large router. The ISP is connected to that same router and all the wired computers connect flawlessly. The wireless router is connected into one of the same ports in that big router that the other computers in the lab are connected to. The windows boxes on the wireless network connect flawlessly through  DHCP. Now my wireless ubuntu notebook will not. I have it set to DHCP and the nameserver is still set to the same thing as the windows boxes. Is there some configuration I am missing? Should the wireless router be plugged into one of the same type of ports on the main router the the ISP connection is in? One thing I did notice when running ipconfig /all on the windows machine was the node type is hybrid. But on the wired boxes is listed as unknown. Is there some setting I have to do to have the notebook recognize the wireless router and then the ISP router or something? I am quite confused at this point...

---

### Post by PaulFr on 2007-08-03
I am a bit confused, is torrent still working ? or is your Ubuntu laptop now completely off the network ?

If it is off the network, and it only has a wireless card, then the starting point is to post the card model and output of the commands: **ifconfig** and **iwconfig**. There are many documents on wireless configuration at **[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)**.

Maybe you can start with **[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)**

---

### Post by BKK on 2007-08-03
no torrent doesnt work anymore...nothing does. I can't get online from notebook so I'll tell you what looks odd to me in the ifconfig is something called eth1:avah. in there is an address that doesn't make sense, as its nothing like what is on the windows boxes. it also has the eth1 listing and eth0 listing, no addresses present in either.

iwconfig lists the proper Essid and looks ok to me...

---

### Post by PaulFr on 2007-08-03
The magic of Avahi (**[http://en.wikipedia.org/wiki/Avahi_%28software%29](http://en.wikipedia.org/wiki/Avahi_%28software%29)**) :

Please see **[http://ubuntuforums.org/showpost.php?p=3013656&postcount=2](http://ubuntuforums.org/showpost.php?p=3013656&postcount=2)** on how to remove it.

---

### Post by BKK on 2007-08-03
Thanks very much, I shall try that on Monday.

---

