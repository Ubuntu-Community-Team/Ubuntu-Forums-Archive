---
title: "Slow wireless connection (linksys pcmcia card)"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by ptnewby on 2008-06-20
I all, I have just installed ubuntu 8.4 onto my laptop wireless internet is working perfect apart from the connection speed i am getting is very slow.

when i check my connetion info m speed is only 1-5 mb/s max

it also says 802.11 WiFi (wlan0) my card is 11g is there some setting i need to change? to allow upto 54mb?

many thanks

---

### Post by chili555 on 2008-06-20
Please try, in a terminal:```
sudo iwconfig wlan0 rate auto
```

---

### Post by ptnewby on 2008-06-22
Hi, ive tried doing as suggested with no avail :-( i'm still only connecting at 1MB per second? could it be i need to install or update the drivers? using a linksys WPC54G ver 1.2

thanks again

---

### Post by ptnewby on 2008-06-26
Any one have any ideas or able to help…?this is driving me nuts!!

---

### Post by Arcadian on 2008-07-01
Change the above command from "sudo iwconfig wlan0 auto" to "sudo iwconfig wlan0 54M". I've just tested the auto setting myself & it sets you back to 1Mb/s. Make sure you reconnect to your wireless network after setting it to 54Mb/s to get the new rate (via Network Manager icon, then check rate under Connection information). BTW, this doesn't seem to stick after a reboot, I'm working on that...

Hope it helps :)

---

### Post by Arcadian on 2008-07-02
Okay, found it here [http://ubuntuforums.org/showpost.php?p=5196903&postcount=16]("http://ubuntuforums.org/showpost.php?p=5196903&postcount=16")

Running "sudo gksudo gedit /etc/network/interfaces" it now looks like this...

```
auto lo
iface lo inet loopback

pre-up iwconfig wlan0 rate 54M
```

So, when I now startup & login for the first time, I get 54MB/s on my wireless every time & am happy again! :)

P.s. Disabling IPV6 properly [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4") didn't make much difference here at all, and I've turned the avahi-daemon processes back on too.

---

### Post by rawtin on 2008-07-23
Hi. I tried all the above suggestions and all work except that any bit rate over 1M will shut the wifi down.  Anything I can do?

---

