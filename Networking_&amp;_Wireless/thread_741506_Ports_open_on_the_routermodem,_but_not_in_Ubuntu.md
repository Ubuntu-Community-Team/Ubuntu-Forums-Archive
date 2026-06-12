---
title: "Ports open on the router/modem, but not in Ubuntu"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by bard on 2008-03-31
Hi all! I've been working on this torrent-related port forwarding problem for days, and still no solution. Hopefully someone here knows the answer.

I cannot get Ubuntu (7.10) to actually open ports, no matter what I do. They're forwarded on both my router and modem, and I've verified this through Windows XP, where torrent downloads work just fine (I dual boot). I haven't installed a firewall, and I've also opened the ports via Firestarter (and the terminal as well, thought I'd try both). I've even gone through three different clients just to see if that was an issue, but it isn't. I'm using ports in the 50000 range and my ISP isn't blocking anything. Both my router and modem are accessible while in Ubuntu, but even still, torrent downloads are slow, and port checkers insist everything's closed up tight.

I've been all through these forums as well as around the net, but I just can't find the problem. Any suggestions?

---

### Post by superprash2003 on 2008-03-31
disable the firewall for a few minutes and then check if your speed improves.

---

### Post by carverj on 2008-03-31
Is this a new problem for you?
Meaning, did it suddenly slow or has it always been slow?

---

### Post by bard on 2008-03-31
Firewall on or off, nothing changes.

It isn't a new problem. I've had Ubuntu installed on this box for just over a month and the ports have never opened and downloads have been slow.

edit: Also worth mentioning is that I've tried several sets of ports.

---

### Post by carverj on 2008-04-01
> It isn't a new problem. I've had Ubuntu installed on this box for just over a month and the ports have never opened and downloads have been slow.

If you are able to download using deluge, this means that you have at least one open port, and so this is not your problem. So you are choosing downloads with plenty of seeds?

---

### Post by bard on 2008-04-01
> **carverj said:**
> If you are able to download using deluge, this means that you have at least one open port, and so this is not your problem. So you are choosing downloads with plenty of seeds?
Yep, I've tried a large variety of torrents, each from different trackers and seed numbers. I'll occasionally get a burst of 40KiB/s, but it doesn't last, and that's not even a third of my DSL speed. Plus, checking open ports (using ShieldsUp, or utorrent/ktorrent's web checker) consistently shows the ports I'm trying to use are closed.

---

### Post by puneit on 2008-04-01
I read that you have tried this on Windows XP and it works, but just to make sure from Ubuntu, please check if your ports are properly forwarded by on [www.whatsmyip.org](www.whatsmyip.org)
There is section on Port Scanners. Test your ports and post back results

---

### Post by bard on 2008-04-01
> **puneit said:**
> I read that you have tried this on Windows XP and it works, but just to make sure from Ubuntu, please check if your ports are properly forwarded by on [www.whatsmyip.org](www.whatsmyip.org)
There is section on Port Scanners. Test your ports and post back results
That's interesting. Every port I scan I get a "timed out" result in both XP and Ubuntu. Running the utorrent port checker in XP says the port is open, but the same check in Ubuntu says it's closed.

---

