---
title: "Excruciatingly slow SMB performance."
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by Romanian on 2008-09-19
Hello all,

I've read threads around here about this, but they've all been jargon at a level of Ubuntu knowledge which I haven't yet reached. Basically, my connection from the Ubuntu server that I have to my Windows XP notebook is painfully slow. I can't even stream an SD DVD rip of Indiana Jones (calculated at about 0.7Mbps). Theoretically, I should be achieving speeds of 54Mbps, but even if we take 5% of that ideal speed, I should be able to stream the 0.7Mbps without hiccups. When I transfer files it's even slower (took 20 minutes to transfer a 3MB photo).

I'm wondering if it's something to do with my network or if it's my actual setup of SMB? It's all on a local network, laptop on 802.11n and server on 802.11g.

Thanks in advance,
Romanian

PS
Please use layman terms as much as possible, or hook me up with a step-by-step process.

---

### Post by blastus on 2008-09-20
Lots of people have had performance issues with Samba. I originally started using NFS then decided to try out Samba because of its security. Samba turned out to be ridiculously slow. There was absolutely nothing wrong with my network. After a few days of trying this setting, that setting, and every other option I could read up about, I gave up on Samba and went back to NFS.

The problem is very likely Samba not your network. You could use NFS instead but I don't think NFS works with Windows (there may be a Windows client for NFS I'm not sure.)

---

### Post by warchief_ryan on 2008-09-21
I have never had performance issues with samba. I stream everything from my server box with samba(music, movies, backups, etc), and I have never seen speeds anywhere as slow as your describing. There are tweaks you can do in the smb.conf, maybe that can help but I think there might be a bigger issue.
 
I wouldn't think its solely sambas fault, but maybe it is.

---

