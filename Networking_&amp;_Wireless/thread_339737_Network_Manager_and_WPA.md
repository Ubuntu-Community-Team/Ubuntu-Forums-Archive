---
title: "Network Manager and WPA"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by Graham1 on 2007-01-16
Is anybody here using Network Manager and WPA successfully? I've been trying for ages to get this setup working but still no joy :(. I'm using a static IP (if that makes any difference) and this setup works in both openSUSE 10.2 and FC6. What am I doing wrong?

:)

Edit: I've noticed that Ubuntu's version is 0.63 whereas FC6 is 0.64 (not sure about openSUSE). Could this be the problem?

Also, could someone tell me where Network Manager saves it's settings?

---

### Post by cpsalvestrini on 2007-01-16
Digging on the Ubuntu forums I found a kind soul who had compiled a debian package for NetworkManager version 0.7.0, including VPN support. This version works beautifully, and is what I'm currently using.

---

### Post by netztier on 2007-01-16
> **Graham1 said:**
>  I'm using a static IP (if that makes any difference)

It does make a difference. 

Any interface you want managed by Network-Manager must be commented-out in [FONT="Courier New"]**/etc/network/interfaces**[/FONT], and therefore you can't use that configuration file to configure static IP addresses. Neither can you use the GUI (System - Administration - Networking) because this is just a frontend for that same config file.

To my current knowledge, Network-Manager does not support static IP addressing - or I just haven't discovered how to do it. If you need quasi-static IP addressing (for instance because you have to enter this interface into some access list somewhere), configure your WLAN adapter for DHCP and use a "static" lease reservation on your DHCP server or a very long lease time.

best regards

Marc

---

### Post by handaxe on 2007-01-16
Hi,

Not an answer to your query, but take a look at :

[http://ubuntuforums.org/showthread.php?t=299462](http://ubuntuforums.org/showthread.php?t=299462)

Connection-manager works with WPA (providing your wifi card  behaves) and it also supports static IPs.  New version due out shortly.  Wide array of other encryption  types due  in new version.  This is a newish initiative and a fine contribution IMO.

The thread is long with loads of info, so read it before you do anything if it takes yer fancy.

HA


> **Graham1 said:**
> Is anybody here using Network Manager and WPA successfully? I've been trying for ages to get this setup working but still no joy :(. I'm using a static IP (if that makes any difference) and this setup works in both openSUSE 10.2 and FC6. What am I doing wrong?

:)

Edit: I've noticed that Ubuntu's version is 0.63 whereas FC6 is 0.64 (not sure about openSUSE). Could this be the problem?

Also, could someone tell me where Network Manager saves it's settings?

---

### Post by Graham1 on 2007-01-16
> **cpsalvestrini said:**
> Digging on the Ubuntu forums I found a kind soul who had compiled a debian package for NetworkManager version 0.7.0, including VPN support. This version works beautifully, and is what I'm currently using.

Would you happen to have a link to this version?

:)

---

### Post by Graham1 on 2007-01-16
> **netztier said:**
> Any interface you want managed by Network-Manager must be commented-out in [FONT="Courier New"]**/etc/network/interfaces**[/FONT], and therefore you can't use that configuration file to configure static IP addresses. Neither can you use the GUI (System - Administration - Networking) because this is just a frontend for that same config file.

I have tried the above but I am never able to get two green lights (just the bottom one). Does Network Manager save it's settings somewhere? I have found the location for FC6 but this does not match up in Ubuntu :(.

---

### Post by Graham1 on 2007-01-16
> **handaxe said:**
> Connection-manager works with WPA (providing your wifi card  behaves) and it also supports static IPs.  New version due out shortly.  Wide array of other encryption  types due  in new version.  This is a newish initiative and a fine contribution IMO.

I may give this a go if I have no joy with 0.7.0. Do you know whether Connection Manager supports DHCP and static IP's?

:)

---

### Post by spd106 on 2007-01-16
Have you read this [http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#head-c8b3f6905f51eed368b9c21893edabcc82531bbc](http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#head-c8b3f6905f51eed368b9c21893edabcc82531bbc)?

I use wpa_supplicant from the interfaces file and I've seen many other have to do this for multiple phase authentication, particularly for 802.1x networks (companies, some universities). NM 0.7 should be good when it's stable enough for a release, I do hope that's soon though.

---

### Post by Graham1 on 2007-01-16
> **spd106 said:**
> Have you read this [http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#head-c8b3f6905f51eed368b9c21893edabcc82531bbc](http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#head-c8b3f6905f51eed368b9c21893edabcc82531bbc)?

I use wpa_supplicant from the interfaces file and I've seen many other have to do this for multiple phase authentication, particularly for 802.1x networks (companies, some universities). NM 0.7 should be good when it's stable enough for a release, I do hope that's soon though.

Thanks for the link :). I'm currently using the same setup, commenting out these lines when connecting to DHCP, restart and then I'm connected. Hopefully 0.7.0 will be released soon.

:)

---

### Post by Graham1 on 2007-01-16
I've got Connection Manager up and running at the moment and it looks like it will suit my needs :D. Will run with this for the time being (currently using DHCP) but will test with a static IP tommorow.

:)

---

### Post by usererror on 2007-01-28
I've got it working with my WPA setup at home.

Would love if it supported all the other protocols like EAP-FAST, LEAP, etc. someday. :D

---

