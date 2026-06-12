---
title: "Network-Manager can't connect to unencrypted networks"
date: 2006-07-22
forum: Networking &amp; Wireless
---

### Post by mempf on 2006-07-22
I have a bcm4318 wireless card. I am using ndiswrapper and network-manager-gnome.

I can connect perfectly to wep and wpa networks. However I can not connect to unencrypted networks.

How can I get it working with unencrypted networks?

Thanks

---

### Post by rekahsoft on 2006-07-22
That is wierd...i have the same card and have experianced the same problems...for some reason the router blocks me when the network is not encrypted (last time i checked)...very wierd...i would say the best fix is to encrypt your network (this will make it work and make it secure so you won't be loosing out on anything)...i think it may be a bug in ndiswrapper...if you get it working some how let me know ;)

---

### Post by mempf on 2006-07-22
Problem is my router does not support wep and I have devices that can't use wpa.

---

### Post by phillip181 on 2006-07-22
I have had this problem for a while. The really affects me when I am going to coffee houses or I am on the road at hotels. I have been working on trying to fix it for a while. This is what I have found. 

First here is a link to a bug posting but it hasn't been solved. [https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/42504]("https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/42504")

Second, from what I can tell from the syslog, it seems that it is a combination of the Networkmanager and WPAsupplicant. I think what is happening is that the DHCP isn't assigning an IP address. And something with BSSID. 

I have WEP at home and it works. I haven't tried WPA. 

This has been annoying for me because it is the last major bug on my Ubuntu laptop.

---

### Post by phillip181 on 2006-07-26
Something else that I noticed. I am connect with NM to my home network that has WEP. I tell it to connect to a neighbors network which is unencrypted. The network monitor goes low and then back up but NM can't connect. It then automatically tries to connect with my home network. It network monitor shows full signal but won't connect and NM doesn't connect to anything. I then manually tell NM to connect to my home network and NM then connects fine. 

Does that tell anybody anything?

---

