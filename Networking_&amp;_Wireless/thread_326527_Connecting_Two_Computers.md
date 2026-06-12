---
title: "Connecting Two Computers"
date: 2006-12-27
forum: Networking &amp; Wireless
---

### Post by voodoonirvana on 2006-12-27
I just got a brand new HP Pavilion dv6000 for Christmas, so obviously this thing has Windows on it. I'll probably dual boot dapper and XP when I find the time to do it. Well on this computer I have Dapper, along with all my personal documents, music, bookmarks, everything. So all I want to do is connect these two computers so that I can transfer all my stuff over to the new computer. I don't know a whole lot about networking or anything but I know enough that if someone were to help me, I could get through it. I have a normal phone line chord, I have an Ethernet cable. I don't know if I should do all this wirelessly or with cables. Both of these computers are on the same wireless Windows network, connected to the same router wirelessly.

---

### Post by kidders on 2006-12-27
Hi there,

How best to do it depends on what you want. For instance, if your filesharing is to be Windoze compatible, you only have one choice ... Samba. Naturally, wired connections are preferable, since they're significantly faster, but you may prefer, for simplicity's sake to use your pre-existing wireless network.

My suggestion is to install and configure a Samba server on your Linux machines, so they can talk to eachother, and to MS operating systems too. Once you're done, you could probably add something like **//server/sharename /home/username/shared smbfs username=whatever,password=whatever,noauto 0 0** to your Linux box's /etc/fstab.

If you don't need Windows compatibility, I would probably opt for NFS, personally. For speed, either a crossover cable or a wired connection through a hub or router would be best.

---

