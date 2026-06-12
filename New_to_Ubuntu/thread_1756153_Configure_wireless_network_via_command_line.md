---
title: "Configure wireless network via command line?"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2011-05-11
Hello! I have an older laptop that I'm considering putting Ubuntu Server on, the only problem is that it will only have wireless network access, and I have no idea where to begin setting up wireless on Ubuntu Server. My ideal end-result would be having the "server" connect to my router automatically upon every boot. Additionally, there would be a way to get it to reconnect automatically if the connection were ever dropped. Is there a way to go about doing this with, say, /etc/network/interfaces maybe? I know that if I were to unplug the Ethernet from one of my hardwired servers and then plug it back in, it's smart enough to reconnect to the network. Can Ubuntu Server do this with wireless too, even without nm?

Any information would be helpful, especially a link to a good, updated how-to, I can't seem to find a decent one.

Thanks in advance!

---

### Post by powerpleb on 2011-05-11
As long as your wireless card is up and running it actually isn't all that hard.
All you really need to do is add an entry to /etc/network/interfaces

```
auto wlan0
iface wlan0 inet dhcp
wireless-essid   <essid>
wireless-key     <key>
wireless-channel <channel>
wireless-mode    managed
```

Have a look here for a more comprehensive guide: [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by pi.boy.travis on 2011-05-12
> **powerpleb said:**
> As long as your wireless card is up and running it actually isn't all that hard.
All you really need to do is add an entry to /etc/network/interfaces

```
auto wlan0
iface wlan0 inet dhcp
wireless-essid   <essid>
wireless-key     <key>
wireless-channel <channel>
wireless-mode    managed
```

Have a look here for a more comprehensive guide: [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

Fantastic! Thanks!

---

### Post by geazzy on 2011-05-12
> **powerpleb said:**
> As long as your wireless card is up and running it actually isn't all that hard.
All you really need to do is add an entry to /etc/network/interfaces

```
auto wlan0
iface wlan0 inet dhcp
wireless-essid   <essid>
wireless-key     <key>
wireless-channel <channel>
wireless-mode    managed
```

Have a look here for a more comprehensive guide: [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)


I'll save it...
maybe one day will need it

thanks....

---

