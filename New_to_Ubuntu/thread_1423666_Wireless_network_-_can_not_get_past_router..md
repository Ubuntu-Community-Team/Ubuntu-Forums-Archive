---
title: "Wireless network - can not get past router."
date: 2010-03-06
forum: New to Ubuntu
---

### Post by PhilBiker on 2010-03-06
Hello, please be patient with me I am very new to Ubuntu.

I have an old Dell Inspiron 3800 laptop that I'm trying to set up as a simple wireless netbook.  I have a new wireless networking card that I was able to use under Windows XP for some time, with some problems.  My XP installation was bad, the disc had some minor failures which meant it needed to be re-formatted.  So I now have Ubuntu.  I don't know if my trouble with the networking was with my corrupt XP installation or the card itself.  It's based on a Ralink chipset.

My network card is kind of screwy.  It won't work in automatic mode, but will connect fine in manual.  I had similar problems with it in Windows XP.  If I'm wasting your time with bad hardware I don't mind if you reply - "get a working network card".

Anyways - here's my problem.  I have wireless networking set up, and it connects.  I can get to the router and I can bring up the router control panel in Firefox.  I can also ping other computers on the local network using their ip addresses.  However, if I try to ping outside the router I get the message "connect:Network is unreachable".

In my manual IPv4 Settings I have the following:

Address: an address within the range of my DHCP IP pool
Netmask: The value for "Subnet Mask" from my router
Gateway: The value for "Default gateway" from my router
DNS Servers: The two addresses for "DNS Address" in my router control panel, separated by a comma (is this the correct delimeter?)
Search domains: Nothing (what is this?)

The computer connects through the wire no problem, but wireless won't get beyond the router.  Connects to the router fine both ways.

Thanks if you can help.  I tried disabling IPv6 as described here: [https://help.ubuntu.com/9.10/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-connection](https://help.ubuntu.com/9.10/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-connection) but the file it asked me to edit came up blank.

---

### Post by wojox on 2010-03-06
You can disable ipv6 here: [http://wojox.homelinux.net/?p=4](http://wojox.homelinux.net/?p=4)

If you open a terminal and run:

```
lspci | grep -i net
```

What does it say?

---

### Post by PhilBiker on 2010-03-06
Thanks for responding so quickly.> **wojox said:**
> You can disable ipv6 here: [http://wojox.homelinux.net/?p=4](http://wojox.homelinux.net/?p=4)

If you open a terminal and run:

```
lspci | grep -i net
```

What does it say?it gives me information on the network card - looks good.  

Here's another page that tells me to turn off ipv6: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#ipv6](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#ipv6) but it gives me the same pointer to a nonexistent file.

I tried the link you suggested explained to turn off IPv6 and now instead of getting Network is unreachable I'm getting 

From: xxx.xxx.x.xx .... Destination Host Unreachable

So curious that I can get to the router but can't get to the internet.
I guess that's better than what I was getting before.

Every troubleshooting guide I've found assumes that if you can get to the router you are connected.  I can connect to the router, and I can ping other computers on the network, and they can ping my computer, but I can't get past the router on this connection.  Is this strange?

I would love to see a document that explains what all the network connections are supposed to be.  F1 does nothing.  It seems every OS and every router uses different terminology "Gateway" "Default Gateway" etc...

---

### Post by PhilBiker on 2010-03-07
I am giving up on the Ralink network card that I got on ebay for $5.  Ordered a more legit network card at Tiger Direct, we'll see how that does.  Thanks to anyone who's reading.

---

### Post by PhilBiker on 2010-03-13
> **PhilBiker said:**
> I am giving up on the Ralink network card that I got on ebay for $5.  Ordered a more legit network card at Tiger Direct, we'll see how that does.  Thanks to anyone who's reading.I got another network card from TigerDirect and appear to be good to go.  The problem apparently was a broken wireless network card.

---

