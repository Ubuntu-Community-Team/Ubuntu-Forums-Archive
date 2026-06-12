---
title: "Azureus stops downloading after a while"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by WerX on 2007-06-19
Invariably my torrents stop after an hour or so in Azureus. My network connection is still working fine and restarting Azureus causes the torrents to begin again, but this is very inconvenient. There are no error messages, NAT light stays green, ports are forwarded properly. I think the problem might not be limited to Azureus but to all bittorrent clients I try but I need to run some others for a bit longer to find out. Has anyone had a similar problem or know what the problem might be?

---

### Post by Biggus on 2007-06-19
It couldn't be that your ISP is cutting your connection after an hour of heavy downloading or something?

---

### Post by WerX on 2007-06-19
No its definately not that. It works fine under windows, and I do know my isp limits my speed during peak hours, but it never stops altogether, and I was testing outside of peak hours early in the morning.

Also the speeds i get under ubuntu seem to be much less than under windows.

---

### Post by Sarke on 2007-06-26
I have the same problem with transfers stop after a while (a soon as 5 min after).  I know it's not the connection or whatever because everything else is fine and I never had the problem with Azureus in Windows.

---

### Post by Sarke on 2007-06-26
I found another BT client that does what I want called Deluge.  It's sort of like uTorrent, and has encryption which I need (damn ISP...).  Anyways, link:

[http://deluge-torrent.org/](http://deluge-torrent.org/)
[http://download.deluge-torrent.org/stable/ubuntu/feisty/](http://download.deluge-torrent.org/stable/ubuntu/feisty/)

---

### Post by chang47 on 2007-06-30
Hello,

I had the same problem before.  My problem was solved by downloading the latest versions of  Java Runtime 1.6 from Sun and Azureus 2.5.0.4.

Sun [http://www.java.com/en/download/manual.jsp#lin](http://www.java.com/en/download/manual.jsp#lin)
Azureus [http://azureus.sourceforge.net/](http://azureus.sourceforge.net/) 

See here [https://answers.launchpad.net/ubuntu/+questions?field.search_text=azureus&field.sort=by+relevancy&field.sort-empty-marker=1&field.actions.search=Search&field.language=en&field.language-empty-marker=1&field.status=Open&field.status=Needs+information&field.status=Answered&field.status=Solved&field.status-empty-marker=1](https://answers.launchpad.net/ubuntu/+questions?field.search_text=azureus&field.sort=by+relevancy&field.sort-empty-marker=1&field.actions.search=Search&field.language=en&field.language-empty-marker=1&field.status=Open&field.status=Needs+information&field.status=Answered&field.status=Solved&field.status-empty-marker=1)

for a bug report on Azureus on Ubuntu 6, it is similar for 7.01. 

Good luck.

---

### Post by bettyhills on 2007-08-04
**Thank you**, Chang47.

---

