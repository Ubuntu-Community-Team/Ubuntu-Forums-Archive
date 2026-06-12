---
title: "Wireless Networks Gone"
date: 2015-07-07
forum: Networking &amp; Wireless
---

### Post by Timoteo32 on 2015-07-07
Help! I'm traveling and all the sudden all my wireless network options are gone. my laptop was working fine, I closed it and came back a couple hours later.  now I have no wireless options. I can't post output because I have no way of connecting to the internet and I have to post this from my phone.

When I run nm-applet it just freezes up my terminal window.  When I type rfkill list wlan, the network manager tool says the state is asleep and wlan state is "unmanaged". It's not hard or soft blocked. Stuff does show up under lspci.

---

### Post by Timoteo32 on 2015-07-07
Also, "notification area" is greyed out when I try and add that to my panel.

---

### Post by PaulW2U on 2015-07-07
*Thread moved to **Networking & Wireless**.*

---

### Post by MGrowl on 2015-07-07
What about restarting network-manager? 

```
sudo service network-manager restart
```

or

```
sudo /etc/init.d/network restart
```

---

### Post by Timoteo32 on 2015-07-08
It gave me:

Network-manager stop/waiting
Network-manager start/running, process 2141

nothing seems different

---

### Post by Timoteo32 on 2015-07-08
I lied, under iwconfig, it now says "managed" but nm-applet still freezes my terminal and notifications area is still greyed out under my panel options.

For what it's worth, I didn't realize my profile was showing my old version. I'm running Ubuntu 14.04 (14.04.2 to be exact), not 12.04.

---

### Post by MGrowl on 2015-07-10
How's the wifi? Were you able to fix it?

---

