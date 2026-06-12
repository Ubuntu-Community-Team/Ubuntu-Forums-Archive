---
title: "Can only connect to encrypted networks"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by Gyatak on 2007-09-11
Hi all,

I have a very strange wifi problem. I'm using Kubuntu Feisty, and I can connect to my home WEP-encrypted network and my work WPA-encrypted network just fine.

However, I can't fully connect to public, unauthenticated networks. I've tried everything I can imagine, but no luck in any free wifi coffeeshops. It's very frustrating. Funny thing is, when I try (I've had most luck using "Wireless Assistant: Wireless LAN Manager"), it appears to connect to the DNS server. I can ping the gateway successfully, and if I try to ping an external domain name, it resolves the address but no packets make it back and neither browsers or email apps have success connecting anywhere.

BTW, I've tried using KNetworkManager, but it hangs on establishing the connection.

I'm using GuardDog (firewall), but it is not doing anything to limit protocols.

Any ideas?

Thanks!

---

### Post by jeremy on 2007-09-30
I have exactly the same problem on kubuntu gutsy beta, and had it before on feisty. Intel Wireless 3945ABG. I have tried with both Knetworkmanager and kwifimanager, exactly the same thing happens.

---

### Post by jeremy on 2007-09-30
The command:
sudo dhclient eth1
will connect it, having logged out from and back into KDE.

---

### Post by cmnorton on 2007-09-30
> **jeremy said:**
> The command:
sudo dhclient eth1
will connect it, having logged out from and back into KDE.

Does invoking this command bypass the regular wireless network is associated with a passphrase? Was a second interface added for non-encrypted networks?

I as trying to infer that from the original problem.

---

### Post by cmnorton on 2007-09-30
Thanks for posting your answer. My laptop -- inherited from my boss -- turned out to have a built in WiFi card, and I did not know about it.

---

### Post by Gyatak on 2007-09-30
> **jeremy said:**
> The command:
sudo dhclient eth1
will connect it, having logged out from and back into KDE.

Yes. That does seem to work. I've now uninstalled all wireless network utilities except KNetworkManager, and without manually entering the command you recommended, I can't get it to connect. 

I had installed other wireless connectors hoping to find something that would connect to WPA protocol. I used WifiManager to establish these connections. Now that I have uninstalled it,  KNetworkManager seems to remember them. That's cool, but also strange.

Is there some alteration to a config file I can make to have KNetworkManager connect to unencrypted networks on its on?

BTW, I found that this suggested sequence of commands (posted in another thread) enabled me to connect to unencrypted networks without relogging into KDE:

> sudo ifconfig wlan0 down
sudo ifconfig wlan0 0.0.0.0
sudo killall dhclient dhclient3
sudo rm /var/run/dhclient.pid
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo ifconfig wlan0 essid <"ESSID_in_QUOTES">
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

---

### Post by Gyatak on 2007-12-11
Just wanted to let everyone know that a lot of this problem was solved by replacing KNetworkManager with Wicd...

---

