---
title: "VSFTPD SFTP speeds from outside network cap at ~1.3mbps"
date: 2017-12-25
forum: Networking &amp; Wireless
---

### Post by mike689 on 2017-12-25
System: ubuntu Server 17

So my SFTP transfer speeds via VSFTPD are getting capped at 1.3/1.4mbps when transferring to a connection outside of my home network, where the server is located. (For instance, transferring from my server, which is on my home connection, to my filezilla client at work, it caps at ~1.4mbps.) This issue repeats with any FTP client I use.

When transferring via SFTP within my home network I get speeds of 10mbps+, but outside they are much slower. The SFTP connection connects fine and it is set to connect on a higher port that is not commonly used by anything.

Could it be my ISP that is somehow throttling the transfer speeds? Is there anything else I can try to change within VSFTPD or my router settings to try and fix this issue?

Thanks in advance!

---

### Post by mike689 on 2018-01-05
I'm still trying to figure this out and google searching brought me back to this post with no answers hah!

Anyone have any suggestions? Is it my ISP throttling it? Some setting I need to change in my router or firewall?

(By the way I've tried using regular FTP as well, still caps at 1.4mbps).

Please help!

---

### Post by Holger_Gehrke on 2018-01-06
Your LAN runs at 100 m**bit** or so, quite normal, even a bit on the slow side (depending on whether you're using a wired or wireless connection; wired can go up to a gigabit/s, wireless 802.11n can deliver 200mbit+ depending on local conditions). Your internet-connection (wide area network) runs at whatever speed you're paying your ISP to deliver, the more you pay the more your get, usually. If the numbers you're quoting are mega**byte** per second than it works out to about 16mbit/s (protocol overhead and error-correction/dropped/damaged packets included). If that's what your contract with your ISP says, then everything is as it should be. If you've contracted for more (and your contract doesn't include some clause along the lines of 'up to (insert speed here) depending on (insert technical conditions and limits)' you should contact your ISP.

Holger

---

