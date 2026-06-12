---
title: "help with torrent download speeds"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by flatline on 2008-08-30
Ok - got my server setup, Torrentflux is running.  **The download speeds are killing me though**!  I am on a FIOS connection - 15Mbps up and down.  When my server ran Win2k3, I got 1000kbps+ downloads, and I wasn't even port forwarding!

With torrentflux initially, I couldn't get anything above 4kbps.  I started forwarding ports 49160-49300, and now my speeds are between 2-120kbps.

I am running Server 8.04 x64 - is there anything I need to do with iptables to help my downloads?

As always, thanks!

---

### Post by flatline on 2008-08-30
Ok, after a little more research it looks like iptables shouldn't be blocking anything.  My iptables config is empty:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```
So I'm still not sure why I'm getting a tenth of the speed I used to.  I don't think that this is isolated to a bad torrent, as I've tried quite a few:
```

119.2kbps  Seeds: 68+27.999  Peers: 111
111.4kbps  Seeds: 53+12.999  Peers: 154
77.6 kbps  Seeds: 14+6.998   Peers: 41
```
I would really appreciate any ideas that could help with this, as I'm paying for 15Mbps.  I'm not expecting to find peers that will upload that fast, but from experience I know that I should be able to get at least 500+ kbps pretty reliably...

---

### Post by flatline on 2008-09-01
bump

could really use any hints.  growing to love torrentflux's interface and loathe its performance...

---

### Post by mellowd on 2008-09-01
Are your ports currently forwarded?

---

### Post by flatline on 2008-09-01
> **mellowd said:**
> Are your ports currently forwarded?

Near as I can tell, I setup my router (Actiontec MI-424-WR) to forward ports 8080 and 49130-49300 to my torrent server.  Before I did that, I couldn't get speeds above 2 or 3 kbps.  

I'm getting between 10 and 100 kbps now, but I know that it should be faster.  On this same box last month when I had Windows Home Server installed, uTorrent got over 1000kbps with NO port forwarding...

It's kind of upsetting, because while I hated WHS, it was super-easy to setup TVersity and uTorrent, and they worked perfectly.  I love Ubuntu, but it has been kind of a pain to get Fuppes and torrentflux working, and they're still not functioning right.

---

### Post by mellowd on 2008-09-01
Remember uTorrent can use upnp (which also happens to be a huge security hole)  so maybe that's why you didn't need to forward ports.


Have you tried a few other torrent clients? Maybe it has something to do with the config of this one. Testing it with another will tell you that much

---

### Post by flatline on 2008-09-01
> **mellowd said:**
> Remember uTorrent can use upnp (which also happens to be a huge security hole)  so maybe that's why you didn't need to forward ports.


Have you tried a few other torrent clients? Maybe it has something to do with the config of this one. Testing it with another will tell you that much

Well great... I downloaded six different torrents with plenty of peers and couldn't get anything above 120kbps.  My roommate downloaded a single torrent and it came down at 1400kbps.  Lovely.

---

### Post by doas777 on 2008-09-01
when I see a torrent going at 120KBps I'm usually pretty happy about it. I've never seen a 1.4MBPS torrent before, but I'm sure they exist. do you mean bits or bytes with 'kbps'? usually Bytes uses a captial B.

personally, I use azureus, and i have UPNP turned off, so I tell asureus to use port 9999 for incoming connections. I then tell my router to forward port 9999 incomming (on both TCP and UDP) to my torrent host on port 9999. I also add an allow-rule to allow incomming connection requests to my public 9999 port.

the upper range ports you mention (40000+) should be used to handle established connections so you should not need to forward them if you are using a statefull firewall on your router ( blocks all incomming connections that are not a response related to a connection initiated from inside the firewall) as is standard these days.  

check out this site. they have lots of info on port forwarding and firewall configurations. 
[http://portforward.com/](http://portforward.com/)

good luck,
frank

---

### Post by sunil237 on 2008-09-07
took me a few days to find the right code but

sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT

replace 6881 with a 50000~ number and thats the port you change your bit torrent to. other cosed i found said invalid synapse or somethnig this one says nothing but when testing with torret = OK :)

.. managed to boost my speed to 200kb~ for a few mins and then it went and my port closed and now my code won't let me open ports again..
any advice for me now?

---

### Post by utorrentuser on 2008-10-10
hi - i have the same issue. on my XP box, its fast as 1MB a second. But on ubuntu, its slow to 10K. I get over 10,000 seeds, but only 6 connection after 30mins. and that is it...

---

