---
title: "How to access modem's web GUI without unpluggin the router?"
date: 2017-11-12
forum: Networking &amp; Wireless
---

### Post by lex24 on 2017-11-12
Is it possible to access modem's web GUI without unplugging the router (and connecting the modem directly to the computer)? The following command won't work:

```
~$ sudo route add -net 192.168.1.254 netmask 255.255.255.255 gw 115.63.160.123

  

SIOCADDRT: Network is unreachable
```

Here is the layout:

```

(WAN, no IP address)
Modem SpeedTouch 516v6 - in bridge mode
(LAN, 192.168.1.254)

(WAN, ISP assigned)
Router Linksys BEFSX41
(LAN, 192.168.2.1)

```

I have changed Linksys' LAN address from the default **192.168.1.1** to **192.168.2.1** to prevent conflicts with modem's LAN address (**192.168.1.254**).

For now, in order to access modem's web GUI I need to disconnect the router and connect the modem directly to the computer, then boot to Windows XP and change the TCP/IP Properties as follows:

```

IP address: 192.168.1.10
Subnet mask: 255.255.255.0
Default gateway: 192.168.1.254

```

Then modem's GUI can be accessed from the web browser using:

```
192.168.1.254
```

And the modem's interface looks as follows:

[https://i.imgur.com/1JB0uXl.png](https://i.imgur.com/1JB0uXl.png)

After the router gets reconnected its routing table looks as follows:

[URL="https://imgur.com/07GUsGU"]https://imgur.com/07GUsGU

[/URL]And here is its Status page:

[https://i.imgur.com/GiTu1Lv.png](https://i.imgur.com/GiTu1Lv.png)

[https://imgur.com/nMMdjUr](https://imgur.com/nMMdjUr)

In the screenshots the first octet of my IP address is greyed-out, let's assume that it is:

[B]115.63.160.123

[/B]-----
Modem: SpeedTouch 516v6, firmware v7.4.3.2
Router: Linksys BEFSX41 , firmware v1.52.15
OS: Arch Linux, Ubuntu v14.04, Windows XP, Windows 7

---

### Post by william.hua on 2017-11-12
It this an AT&T U-Verse Gateway? The IP address looks familiar. Try putting the gateway into bridge mode.

---

### Post by oldfred on 2017-11-13
Router Linksys BEFSX41
(LAN, 192.168.2.1)

I use this in Firefox for router. You have to give name & password, which usually are just defaults.

[http://192.168.2.1/](http://192.168.2.1/)

If modem is from ISP, it may be locked down. Why do you need to access modem, not just router?
And most ISP modems are combination modem/router devices.

---

### Post by lex24 on 2017-11-18
Can someone please confirm that the command shown in my first post (repeated below) is actually correct? Maybe it should be preceded with some other command, or maybe some parameters are missing. As I understand it, after the command has been executed the modem should be accessible through the router:

```
~$ sudo route add -net 192.168.1.254 netmask 255.255.255.255 gw 115.63.160.123
```

192.168.1.254 - modem's LAN address
115.63.160.123 - router's WAN address

Here is the layout:

```

(WAN, no IP address)
Modem: Thomson SpeedTouch 516v6 - in bridge mode
(LAN, 192.168.1.254)

(WAN, 115.63.160.123) - ISP assigned
Router Linksys BEFSX41
(LAN, 192.168.2.1)

```

---

