---
title: "Which is safer for proxies, Socks4 Socks4a Socks5 HTTP or HTTPS?"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by DesiArnez6 on 2009-06-24
If tor and privoxy were already installed,(and working fine on Internet browsers like firefox etc) would there be a way to take advantage of this privacy by applying it to Instant Messaging clients?

I currently use AIM 1.5.286 (for linux) and it gives me 4 different proxy options:

First It says Host: which Id assume is always 127.0.0.1 (I you dont have a network) And then a space or the port,  8118 (for Http?)  9050 for Socks?
There are Four protocol options:
SOCKS 4
SOCKS 5
HTTPS
HTTP

Is there a diference in security? Which is superior? I read stuff about DNS and leaks but I dont understand?



Also, I use Yahoo Messenger 1.0.6 (for Linux) and their is only one proxy option:

HTTP

and then a box for "Server Name" (127.0.0.1)? and a box for "Server Port"

*Bonus note: why are all my yahoo contacts offline? (when they tell me many that they arean't) And I have to re login every few minutes?* Just to throw that in there

*********But main concern is security, so that my messages aren't in just plain view, if Im connected in a public wireless spot in the city, etc

---

### Post by katakaio on 2012-03-09
Resurrecting an old one because I was looking for the same info myself recently. The first thing to mention is the difference between SOCKS and HTTP/HTTPS. SOCKS forwards TCP and UDP connections, while HTTP forwards HTTP requests. A decent comparison between the two protocols in practice can be found [here]("http://en.wikipedia.org/wiki/SOCKS#Comparison"). I recommend using SOCKS whenever possible, as this is the native protocol that Tor uses. (This also means that you can connect to Tor without using another proxy as long as your application has SOCKS support.)

As far as which SOCKS version you want, bodhi.zazen has an [excellent explanation]("http://bodhizazen.net/Tutorials/TOR#socks") of the DNS leak issue in SOCKS4 and SOCKS5. Basically, 4 and 5 use IP addresses to connect, while 4a uses hostnames. If you're seeking more anonymity, SOCKS4a is what you want.

If your application doesn't offer SOCKS4a support, then you must configure your application to first send its request to privoxy (or polipo or whatever local proxy you're using) which will then send its request to Tor via SOCKS4a. Again, bodhi.zazen has a [great walkthrough]("http://bodhizazen.net/Tutorials/TOR#Privoxy") on how to do this.

---

