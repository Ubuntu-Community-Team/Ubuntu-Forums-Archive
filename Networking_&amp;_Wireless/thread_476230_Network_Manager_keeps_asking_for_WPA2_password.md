---
title: "Network Manager keeps asking for WPA2 password"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by pak33m on 2007-06-17
I am on a System76 Gazelle Value laptop and recently upgraded to Ubuntu 7.04 Feisty Fawn and network-manager-vpnc.

I am connecting because I can access the Internet and I get an IP address.  However, Network Manager keeps asking for the WP2 password.  I enter it, I still have an Internet connection and IP address, but keeps asking for the password.

Any help would be appreciated.

---

### Post by spd106 on 2007-06-17
This issue is being worked on upstream and from the Network Manager mailing list I understand that a patch has been committed to 0.6.6 SVN recently. Unfortunately, this won't be coming to Ubuntu 7.04 (Feisty) except perhaps through a backport.

The best advice I can give is to ignore the dialogue box. Though there may be someone else who knows of a workaround.

---

### Post by pak33m on 2007-06-18
If I ignore the dialogue box Network manager either quits or tries to connect to my neighbors wireless network which does not work either.  And it has no security on it!  That is the other thing that I tried, no security on my wireless network, to no avail.  

I have the same results connecting to a ired connection through Network Manager.  I get an IP address but then get dropped just like I was getting with WPA2 and with no security.

I have since been able to get a wired connection static IP address configured in /etc/network/interfaces.

Is there anymore info about this issue: web links, search keywords, etc?  I have nearly exhausted myself and System76 in trying to figure it out!

Also, I noticed that I access System->Admin->Users and Groups, Network or Services any longer.

---

