---
title: "NetworkManager Profiles"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by jazee on 2006-11-14
I am wanting to know were or how can you edit NetworkManager's stored profiles. I want to remove select wireless networks so that it will stop auto connecting to that network. Also is there a way to force it to do a refresh on SSIDs. I really get tired of entering all the connection every time that it misses the broadcast from the router. Thanks

---

### Post by Macchi on 2006-11-14
I have also been looking for something similar for the NM!
Apologizing for the huge risk of being boring and requesting
too much, I will publish here are my requests for a NetworkManager:

1)I would like to be able to blacklist some wireless networks.
This would improve security, for instance to avoid sending passwords over non-secure networks.

2) I would like to add a preference or priority order for attempting connections to networks. This would improve security and performance.

3) Extend wireless management for 3G: I need integration with ppp to be able to use NM with my 3G card for internet access through the mobile networks. 3G connections require further steering with some ppp scripts. Setting priorities to attempt connections first for for Wired, then WiFi and at last 3G networks would avoid the need for any manual intervention.

4) At last but not lest I would also like to trim the Firewalls. This complicates things further, because I have to consider different firewall settings for every type of network connections. May be I should look again at laptop-net, since it could do this job. The problem is that the manual configuration for laptop-net is scattered through many text files. It becomes cumbersome to configure and to maintain. I am looking for the best possible worlds with high flexibility, easy configuration and high security. 

I am sorry to remember that today I can get most of these features directly out of the box through the mainstream OS on the market. But it is sad that it doesn' t work yet with my favorite Ubuntu.

---

### Post by jazee on 2006-11-14
Well I got some information so far from the mailing list. ~/.gconf/system/networking/wireless/networks is the folder were all your profiles are stored at. You can remove the directory that relates to your SSID of the network that you want to remove. This will remove the auto connect. So far thats all I have heard back. So that might help you out a bit. 

Wish I knew a lot of C++ or C# or I would help out with tyring to make it better, but all I got is web languages.

---

### Post by JeremyLong on 2007-10-27
> **jazee said:**
> I am wanting to know were or how can you edit NetworkManager's stored profiles.

Use gconf-editor > system > networking > wireless > networks

> **jazee said:**
> I want to remove select wireless networks so that it will stop auto connecting to that network.

Right click on on the essid of the network and choose 'Unset Key'

---

