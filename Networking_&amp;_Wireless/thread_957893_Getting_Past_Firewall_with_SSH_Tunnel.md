---
title: "Getting Past Firewall with SSH Tunnel"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by terminator14 on 2008-10-24
I have a general question about networking, not really one related to any OS. I download quite a bit over torrent, and since I kind of ran out of my monthly download/upload limit at home, I was thinking I could download stuff at my college. They have 2 T3 lines so their download/upload speeds are insane even compared to the extreme speed internet I have at home, and their monthly limit is slightly larger than mine is I imagine. The only problem is that all their ports are blocked on their firewall. My azureus can't connect to any peers. Doing a quick search online, I found that I could use an ssh tunnel to run the torrents through, so that the connection is no longer blocked.

If I set up an ssh server at home and run torrents from my computer at school through that ssh server, will all the traffic of the downloads go through my home network, wasting my monthly download/upload limit? And will the torrent downloads be limited by my home network's upload speed then?

---

### Post by terminator14 on 2008-10-25
Anyone know what I'm talking about? I'm going by the instructions outlined [here]("http://whalesalad.com/2006/08/27/tunneling-bittorrent-over-ssh/"), except for the part where they say to use an ssh server that clearly states on the main site that they do not wish to be used for torrenting files. That is why I want to setup my own ssh server. 

The site explains how to use a socks proxy through the ssh tunnel to send torrent data through it...

---

