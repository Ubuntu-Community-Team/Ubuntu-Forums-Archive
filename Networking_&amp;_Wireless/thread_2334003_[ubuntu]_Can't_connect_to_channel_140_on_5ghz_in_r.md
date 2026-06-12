---
title: "[ubuntu] Can't connect to channel 140 on 5ghz in regulatory domain RU"
date: 2016-08-15
forum: Networking &amp; Wireless
---

### Post by pellefantus on 2016-08-15
Hello,

I live in Russia and have a asus rt-N77u router set to 5gh control channel 140 (5700 mhz) my macbook, and android phones connects fine to the router but my ubuntu 14.04 LTS does not. I tried to change my regulatory domain to RU, as seen at:
```
$iw reg get
country RU:
    (2402 - 2482 @ 40), (N/A, 20)
    (5735 - 5835 @ 20), (N/A, 30)
```

Wikipedia states that channel 140 is allowed [https://en.wikipedia.org/wiki/List_of_WLAN_channels#5.C2.A0GHz_.28802.11a.2Fh.2Fj.2Fn.2Fac.29.5B17.5D](https://en.wikipedia.org/wiki/List_of_WLAN_channels#5.C2.A0GHz_.28802.11a.2Fh.2Fj.2Fn.2Fac.29.5B17.5D).

Some of my neighbours run routers with countrycodes GB and SE if that matters.

I tried to make a script that changes iw reg set to all countries possible, and none of them show 140 as a selecatble channel. I can connect with 2.4ghz fine though.
[B][URL="https://github.com/UbuntuForums/wireless-info#wireless-info"]
[/URL]Wireless Info:[/B]


[http://hastebin.com/raw/becorugiga](http://hastebin.com/raw/becorugiga)

---

### Post by jeremy31 on 2016-08-15
Search for posts by Pilot6, he also found this issue and the solution

---

### Post by pellefantus on 2016-08-15
which one would that be?

---

### Post by chili555 on 2016-08-15
I suggest that you try the live DVD or USB for Ubuntu 16.04. When I temporarily change the CRDA to RU on my machine, I get:```
$ sudo iw reg get
[sudo] password for chili: 
country RU: DFS-ETSI
	(2402 - 2482 @ 40), (N/A, 20), (N/A)
	(5170 - 5250 @ 40), (N/A, 20), (N/A)
	(5250 - 5330 @ 40), (N/A, 20), (0 ms), DFS
	(5650 - 5730 @ 40), (N/A, 30), (0 ms), DFS
	(5735 - 5835 @ 40), (N/A, 30), (N/A)
	(57000 - 66000 @ 2160), (N/A, 40), (N/A)

```Channel 140 is 5700 MHz and is included above.

---

### Post by jeremy31 on 2016-08-15
Pilot6 reported a bug [https://bugs.launchpad.net/ubuntu/+source/wireless-regdb/+bug/1539448](https://bugs.launchpad.net/ubuntu/+source/wireless-regdb/+bug/1539448)
Said the wireless-regdb was better in xenial(16.04) but not yet correct

---

### Post by pellefantus on 2016-08-16
Thanks for the heads up! I did as proposed [here]("https://askubuntu.com/questions/727593/problem-with-intel-7260-wireless-adapter-on-5-ghz-on-ubuntu-14-04") and it works. Will update the topic to [solved].

---

