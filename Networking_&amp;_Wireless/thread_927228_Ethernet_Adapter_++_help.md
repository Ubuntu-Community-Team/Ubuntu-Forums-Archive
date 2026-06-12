---
title: "Ethernet Adapter ++ *help*"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by tufcamman on 2008-09-22
Hey everyone,

    Here's a wierd one for you!  Every time I restart my computer the name of my ethernet adapter increases by one.  (eth1, eth2, etc)  So pretty soon I'm gonna have eth100.  I have a gateway T-6836 with Ubuntu Hardy Heron installed.  Pre-thanks for any help at all!

---

### Post by Iowan on 2008-09-22
I've seen those symptoms in another thread - I'll see if I can find it.

Oops - guess it was [yours]("http://ubuntuforums.org/showthread.php?t=889819").  I (still) think there was another before that, though.
[Here]("http://ubuntuforums.org/showthread.php?t=615581") is another *somewhat* similar.

---

### Post by gali98 on 2008-09-22
This may help. Taken from aircrack faq (hey that rhymes :))

 Or even to eth2 or from wlan0 to wlan1 or &#8230; You know the symptoms mean if you suffer this problem. This happens when you change your MAC and UDEV thinks it has detected a new network card. UDEV keeps track of this so that your nwc-naming keeps mixed up even after a reboot.

Solution: Disable this function in UDEV

Open /etc/udev/persistent-net-generator.rules in your prefered text editor

Search for

 KERNEL=="eth*|ath*|wlan*|ra*|sta*", DRIVERS=="?*",\
 	IMPORT{program}="write_net_rules $attr{address}"

and change it to

 #KERNEL=="eth*|ath*|wlan*|ra*|sta*", DRIVERS=="?*",\
 #	IMPORT{program}="write_net_rules $attr{address}"

Save and close.

Open /etc/udev/rules.d/z25_persistent-net.rules in your prefered text editor (&#8220;z25_&#8221; may be something different on your system).

Search for the lines concerning your nwc and delete or just disable them by inserting a leading &#8221;#&#8221;.

Reboot and everything should be back to normal and stay there.

Note: If you update udev to a newer revision you may have to do this again

looks straightforward..... Just backup everything...
Kory

---

### Post by tufcamman on 2008-09-22
Marvelous, thanks for all the help!

---

### Post by gali98 on 2008-09-22
Does this means it worked? :)
Kory

---

### Post by tufcamman on 2008-09-22
Yes sir :)

---

### Post by gali98 on 2008-09-22
Good Deal!
:):):)
Kory

---

