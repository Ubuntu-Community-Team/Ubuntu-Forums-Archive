---
title: "Slow network performance with Samba and NFS on wifi and lan"
date: 2019-01-15
forum: Networking &amp; Wireless
---

### Post by pushead on 2019-01-15
Hey guys,

My name is Marius and I'm new to the linux universe and using Ubuntu 18.04 LTS now for over 6 months on my Lenovo L460 Laptop. 
From day one I noticed a significant  disadvantage on networking performance compared to my previous Windows 10 installation.
In numbers I got about 60 Mb/s over wifi and the full gigabit over LAN while sending large/small files under Windows to my Freenas 11.1 server with smb.
With Ubuntu I only got 25 Mb/s and with later updates that dropped down to about 10 Mb/s. I was only using Samba over wifi at that time and suspected the driver for the wifi adapter to be the source of the problem.

Since last week I'm using an all new Kubuntu 18.04 LTS installation. The details of the  wifi connectíon shows me that the connection speed is about 600 Mbit/s or more. When I'm connected to the 2,4 ghz wifi the speed goes down to about 300 Mbit/s.
The connection speed with Samba is about 8,x Mb/s with 5 ghz wifi and the same with Gigabit Lan.
So I tried NFS. Speed got up to 10,x Mb/s. Again same speed with wifi and gigabit.

There are no performance issues while copying files between the installed ssds and external drives. The problem seems to be network related.

Can you help me with that problem?
Thanks in advance.

Marius

---

