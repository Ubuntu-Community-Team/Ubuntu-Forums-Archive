---
title: "question about how to write edit my interfaces file"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by rdg311 on 2007-07-03
I am following this guide on how to get my wua1340 dlink wireless usb working. Everything seemed well except for the fact that i can only use my instant messenger and go to [www.google.com](www.google.com) home page. no other web pages load and i cant actually search anything in google.

i think i may have made a mistake at this section of the tutorial:

Wierdism #2 - I check Ubuntu's Network utility ( System>Administration>Networking ). It said that though wlan0 was present ( and thankfully that wmaster0 was not ), wlan0 was not enabled (!!). I enabled it and entered my essid ID in the properties dialog box. 
By doing that, it wrote this line
wireless-essid my-home-wireless-ID
in the /etc/network/interfaces file under the wlan0 entry that was already there at the end of the file:
auto wlan0
iface wlan0 inet dhcp
wireless-essid my-home-wireless-ID


do i just add the line "wireless-essid my-home-wireless-ID" word for word or do i need to put the name of my essid after wireless and does ID stand for some other ID. Basscially do i write this "wireless-essid my-home-wireless-ID" or "wireless-belkin54g my-home-wireless-some id here". sorry if i am at all unclear.

---

### Post by spd106 on 2007-07-03
If anything works at all then it is unlikely that the problem is with the essid. I suggest you look elsewhere such as proxy settings or maybe IPv6 troubles.

As far as the interfaces line is concerned it should be wireless-essid 'name'. The idea is that the wireless- part means that the command is for the iwconfig tool where the -switch can be any one of the settings iwconfig excepts, e.g. essid, key, channel etc.

My interfaces file used to look a bit like this
```
iface eth1 inet dhcp
wireless-essid linksys
wireless-key 1234567890
```

If you have a space in the essid then wrap it in single quotes or it won't work. The interfaces man page gives a more exhaustive description of the many options.

---

