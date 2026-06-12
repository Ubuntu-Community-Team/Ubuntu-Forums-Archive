---
title: "Anonymity while using a Bit Torrent Client like Transmission"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by suomalainen on 2009-12-22
Ubunteros,

I would like to know if it is possible to maintain my anonymity while using a Bit Torrent client like Transmission.

Currently I have Tor installed cause I'm getting all sorts of spam and junk mail presumable from visited websites I review.

Now I would like to increase my protection.

I heard of Vuze but not sure how it would be used in my case.

Thank you!

---

### Post by JebusWankel on 2009-12-22
Tor might help, though the use of bittorrent over tor is somewhat controversial among the Tor community.

Vuze has probably as wide an array of anonymity features. It can also change the way it sends data so it doesn't look like bittorrent to network admins. Vuze is in the repositories, so you can get it with the Add/Remove application. The settings you would be looking for are kind of deep in the menus, so I recommend the azureus wiki.

---

### Post by bodhi.zazen on 2009-12-22
See : [https://wiki.torproject.org/noreply/TheOnionRouter/TorifyHOWTO/BitTorrent](https://wiki.torproject.org/noreply/TheOnionRouter/TorifyHOWTO/BitTorrent)

Several options listed on that page.

---

### Post by doas777 on 2009-12-22
well, there is no good (legal) way to get anonymity except via a proxy relay network like tor. I2P has a lot of possibility, but it never took off, so noone creates content for it. 

you should encrypt your connections (rc4 or better is best), and a blocklist like iplist, moblock, or the one in vuze provide a limited amount of protection, but is far from perfect, and can be cumbersome.

---

### Post by suomalainen on 2009-12-22
Can somebody explain to me how this TRACKER PROXY is added?

Also, Does anyone know FOR SURE if transmission releases my IP?

Thank you!



BitTorrent

(link)

For bittorrent it is probably not so helpful to torrify data. Compared to the amount of damage you will do to your throughput and the amount of damage you will do to the Tor network, torryfing data is overkill for the protection you gain. Aside from search index logs and tracker http logs, the attacks needed to determine who is downloading a torrent are somewhat similar to attacks on Tor: the adversary has to be running torrent clients and watching to see who connects to them. This is hard to do on a large scale. You are probably much more at risk for showing up in the webserver logs for popular trackers and index sites.

For this reason, you may want to use tor to communicate with the tracker. For this, just add --tracker-proxy 127.0.0.1:8118:

btlaunchmanycurses --tracker_proxy 127.0.0.1:8118 <directory>

Whilst the above may work to some extent, anonymising the client to the tracker means other clients are unable to download from the Torified client. This leaves it functioning as a Leech which severely degrades its performance within the swarm. This issue applies to the Bittorrent protocol in general, regardless of the client software employed.

---

### Post by johndoe32102002 on 2010-07-08
There is an anonymous version of Transmission for I2P for i386 (32-bit Ubuntu installs) on echelon.i2p's website after installing I2P.  This will only allow torrents inside the I2P network and no external websites such as the PirateBay or ISOhunt.

---

