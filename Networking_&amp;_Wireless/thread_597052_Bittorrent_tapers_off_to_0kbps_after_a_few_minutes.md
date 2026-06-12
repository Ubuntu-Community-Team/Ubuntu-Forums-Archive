---
title: "Bittorrent tapers off to 0kbps after a few minutes"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by PartisanEntity on 2007-10-30
I have a strange problem with Deluge, when I start a download all is well for about 5 minutes, then the connection will go down to 0kbps. I will at this point briefly loose the internet connection. Network manager then reconnects, but Deluge remains offline i.e. not downloading anything and not connected to any peers.

I am using wireless, i am behind a wireless router that is connected to my cable modem. Ports are open. I tried ethernet with the same results.

Any ideas?

---

### Post by gb5uqx on 2007-10-30
Is it only torrents that are affected?. Just a thought but you could try enabling transport obfuscation and encryption if Deluge supports it, I know Azureus and uTorrent (will someone please port a Linux version) do. Perhaps your IP is capping or bottlenecking P2P traffic. Otherwise i'm stumped as well.

---

### Post by PartisanEntity on 2007-10-30
Well the encryption is on by default in Deluge, however, after turning on random port selection it seems to have solved the problem. So far I have been downloading since about 20 minutes without any issues.

---

### Post by ThrobbingBrain66 on 2007-10-30
I've read that sometimes ISPs block/throttle ports in the 6000s (which is what I believe Deluge uses by default).

---

### Post by PartisanEntity on 2007-11-07
This is really getting on my nerves, no matter what I try to download and no matter which bittorrent client I use, the connection will, either after 5mins or after about 40mins tapper off down to 0kbps.

I have no idea how test if this is being caused by:

the bittorrent client
ubuntu
my router
the isp

I tested Transmissions last night and it worked the best out of all bittorrent clients I have used so far. But it did tapper off to 0kbps after 50% hed been downloaded and so I had to shut it down, disconnect and reconnect then launch it again to download the remaining 50% of the file.

---

### Post by NHaGa on 2007-11-07
I have this problem as well. I'm really looking forward to getting this solved...

---

### Post by NHaGa on 2007-11-08
Bump... (sorry)

---

