---
title: "VPN? SSH Tunnel?"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by logik3x on 2007-05-28
Hi, I have a box behind a NAT layer which serves as a web development server and bittorrent/storage server. I need to have access to the box from outside to at least the http (80) and ftp/sftp would be a plus. My problem is that I don't have the necessary bandwidth or cpu/memory on my vpn server to handle all all the traffic from that box. One solution would be to get only port 80 on the vpn but is that possible? as for ftp/sftp would it be possible to connect without vpn (save bandwidth) with an SSH tunnel?

Any suggestions are welcomed, please post any experience or input you have!

---

### Post by kidders on 2007-05-29
Hi there,

You haven't given any indication of what you'd like to be able to do remotely, so it's hard to make a suggestion. Chances are though that unless you need to be able to do something that *requires* a VPN (ie there is no other practical way of doing it), then you don't want one. Equally, unless there is a very good reason for *needing* FTP, you probably won't want that either. Unfortunately, your o/p doesn't give much away, so you may well need both!

For most purposes, an SSH server is all that's typically required. Any unreserved port can (I presume) be easily forwarded to the right place by your firewall, to give you access to your development box's SSH server.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

