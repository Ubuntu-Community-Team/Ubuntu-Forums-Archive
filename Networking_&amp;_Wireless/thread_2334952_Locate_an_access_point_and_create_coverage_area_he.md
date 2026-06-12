---
title: "Locate an access point and create coverage area heat map"
date: 2016-08-24
forum: Networking &amp; Wireless
---

### Post by erotavlas on 2016-08-24
Hi,
I work in a school and I would like to locate some access points which position is unknown.
I read many guides about how to do this task. One very interesting guide for linux is this [http://blogs.interfacett.com/finding-rogue-wireless-access-points-kali-linux](http://blogs.interfacett.com/finding-rogue-wireless-access-points-kali-linux)
that combines cheap antenna with the power of kali linux.
I found some stand alone products like this [https://www.anixter.com/en_us/products/AIRCHECK-G2-KIT/NETSCOUT/Data-Test-Equipment/p/704154](https://www.anixter.com/en_us/products/AIRCHECK-G2-KIT/NETSCOUT/Data-Test-Equipment/p/704154), but they are extremely expensive.
Moreover, I would like to have an heat map of coverage area. I found this interesting guide for windows [http://www.howtogeek.com/165614/how-to-create-a-wi-fi-heatmap-for-network-analysis-better-coverage-and-geek-cred-galore/](http://www.howtogeek.com/165614/how-to-create-a-wi-fi-heatmap-for-network-analysis-better-coverage-and-geek-cred-galore/).
Do you have any advice for linux? 
Thank you

---

### Post by chili555 on 2016-08-24
The first link you gave simply uses airmon-ng in Kali linux. airmon-ng is available in Ubuntu or, for that matter, any other Linux distribution I am aware of. It is pretty complex and a bit tricky to set up.

Perhaps you'll consider wifi-radar. [http://wifi-radar.tuxfamily.org/images/wr-v2.x-25-main_win.png](http://wifi-radar.tuxfamily.org/images/wr-v2.x-25-main_win.png) It is available in the Software Center or, for old school users, from the terminal:```
sudo apt-get install wifi-radar
```There is also kismet, which is also a bit tricky to get going: [https://linuxkismet.files.wordpress.com/2008/08/kismet1.png](https://linuxkismet.files.wordpress.com/2008/08/kismet1.png) It's also in the Software Center and, as well:```
sudo apt-get install kismet kismet-plugins
```

---

### Post by Bucky Ball on 2016-08-24
> **chili555 said:**
> The first link you gave simply uses airmon-ng in Kali linux. airmon-ng is available in Ubuntu or, for that matter, any other Linux distribution I am aware of. It is pretty complex and a bit tricky to set up.

... and to add that we do not give support for or allow discussion of it on these forums. ;)

Thanks chili555.

---

