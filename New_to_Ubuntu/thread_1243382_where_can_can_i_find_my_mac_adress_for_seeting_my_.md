---
title: "where can can i find my mac adress for seeting my wifi?"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by heyyy on 2009-08-18
also if you could give me some advise on wireless security would be great.
i just want to set up a simple connection from router to pc without anyone else connecting

---

### Post by halitech on 2009-08-18
just run this
```
sudo ifconfig
``` and it should have the MAC listed there

---

### Post by diablo75 on 2009-08-18
Well if you want the MAC address of your wifi (or even hardline interface like your Ethernet port) open a terminal windows (Applications>Accessories>Terminal) and type the command:

```
ifconfig
```

If you want information even more specific to wifi devices, type:

```
iwconfig
```

The only use I can see that you would have for needing to know your MAC address is if you were to attempt to filter connections on your router by setting a blocking policy for all other MAC addresses, except yours.  However, this alone is not bullet proof as your MAC could be spoofed.

The best form of wireless security you can use is encryption.  Your router should be capable of enabling either WEP, WPA or WPA2 encryption (the latter being the most secure; the former the least secure).  It's best if you set this up over an ethernet connection and once it's enabled then switch to your wireless and use the passphrase you chose during the enabling to authenticate with the encrypted network.  Be sure to create a passphrase that is difficult for others to guess, or contains a variety of characters (Capitalized letters, numbers or symbols like $@!% etc.)

---

### Post by realzippy on 2009-08-18
Install macchanger.

The command:

**macchanger -s eth1**

...eth1 is an example.

Your network devices:

**ifconfig**

**iwconfig**

---

### Post by heyyy on 2009-08-18
on the wifi settings among other it gives the following options:
1)mac filter with MAC Restrict Mode:allow/deny/disabled

2)Wireless -- Bridge with AP Mode:access point/wireless bridge
                          Bridge Restrict:Enabled/Enabled(scan)/disabled
                          Remote Bridges MAC Address:_____________________

being a newbe in wireless,im not exactly sure what are they,could someone give me an explanation those 2...?

---

### Post by 3rdalbum on 2009-08-18
> **heyyy said:**
> on the wifi settings among other it gives the following options:
1)mac filter with MAC Restrict Mode:allow/deny/disabled

2)Wireless -- Bridge with AP Mode:access point/wireless bridge
                          Bridge Restrict:Enabled/Enabled(scan)/disabled
                          Remote Bridges MAC Address:_____________________

being a newbe in wireless,im not exactly sure what are they,could someone give me an explanation those 2...?

MAC filter is part of what you want; it allows you to allow or deny clients based on what MAC address they are connecting from.

Wireless bridging is not relevent for you. It's where you can extend the range of your wireless network by having multiple routers communicating with eachother.

I'm surprised nobody posted the best way of finding out your MAC address: Connect, then right-click on the Network Manager, and then click "Connection Information" and it's under "Hardware Address".

If you want to secure your wireless properly, you need to tell your router to use WPA2 encryption. It might be called "WPA2-PSK" which stands for "pre-shared key"; this is your regular password-login type.

When choosing a password, use uppercase and lowercase letters, symbols and numbers. If you have two passwords that you use interchangably, run them together to create a long password. For instance, this password wouldn't be bad:

TumourSG/1234Head-5

I've put together two passwords: TumourHead and SG/1234-5, which are memorable to me but not on the top list of "passwords to try first when brute-forcing".

---

### Post by heyyy on 2009-08-18
if i "hide" my access point would that be any good ?

---

