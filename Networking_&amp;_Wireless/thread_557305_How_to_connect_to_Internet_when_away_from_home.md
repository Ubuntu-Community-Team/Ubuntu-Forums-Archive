---
title: "How to connect to Internet when away from home?"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by PaulFXH on 2007-09-22
I'm using Ubuntu Feisty on a new MacBook (2.16 GHz).
I had set-up Network manager to work perfectly with both wired and wireless internet connections before I left home (with a lot of help from the Apple Intel section of this forum).
However, now I find myself on the other side of the world and cannot get an internet connection.
Although, where I am, I can pick up as many as 10 wireless networks and indeed actually connect to some of them, when I am connected and try to open (for example) [www.google.com](www.google.com), I get a "cannot locate remote server" error message.
This applies to whatever web page I try to open.
Even with a wired connection, I get the same performance which is that the connection is indicated but I cannot open any web page at all and get the same error message.
What's up with this?

---

### Post by Paris Heng on 2007-09-22
Do you try checking your Wifi and Ethernet interfaces' IP address when you are outside? What you set on the interfaces? Static or DHCP?

---

### Post by PaulFXH on 2007-09-24
Thanks for your reply.
I'm actually using the Roaming Mode for both Wireless and Wired connections.
When I do have a connection to a wireless network, clicking on "Connection Information" gives me all the details about the IP, DNS and other connection addresses.
In addition, I can ping to the router address without problem but nit seems the router is not, as yet, connecting to the outside world.
I really would appreciate some help to get this solved as I'm really at a loss.
Thanks
Pail

---

### Post by SpiritIsReality on 2007-09-24
howdy
maybe you're connecting to networks that don't have internet access.
can you ping [www.google.com](www.google.com) ?
that's about all I've got.
how are you posting here, if you can't connect to the internet?
there must be a way to connect to the router you're using now?
[https://help.ubuntu.com/community/InternetHowto](https://help.ubuntu.com/community/InternetHowto)
[http://aboutdebian.com/](http://aboutdebian.com/)
oh! this router isn't wireless?
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)
[https://wiki.ubuntu.com/NetworkRoaming](https://wiki.ubuntu.com/NetworkRoaming)
I also clicked on search, advanced, keyword, roaming, search titles only,
looks like it doesn't work very good yet.so you could try ...
a bit here after heading, iwconfig before you start
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
and
```
man iwconfig
```
oops, I forgot iwlist, here under heading, getting the goods
[https://help.ubuntu.com/community/WifiDocs/WiFiWithSomeoneElsesRouter](https://help.ubuntu.com/community/WifiDocs/WiFiWithSomeoneElsesRouter)
probably iwlist wlan0 scan ..that's a zero, and
```
man iwlist
```
trails

---

