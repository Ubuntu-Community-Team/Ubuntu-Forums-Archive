---
title: "Port forwarding the easy and proper way."
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by uberlube on 2008-02-23
Can someone suggest a easy to understand and effective tutorial on port forwarding for faster downloads? Much appreciated.:)

---

### Post by ruy_lopez on 2008-02-23
port forwarding for faster downloads? Never heard of that. Port forwarding is for when you want inbound connections to your router forwarded to a machine inside your network.

---

### Post by uberlube on 2008-02-23
....ok. Well my problem is that my torrent downloads have gone down from several hundred  kb/s to like 1 or 2 kb/s. Any thoughts.

---

### Post by ruy_lopez on 2008-02-23
It could be your ISP is throttling traffic to certain sites. Are downloads from other sites okay?

---

### Post by Diabolis on 2008-02-23
Computers use a range of ports to connect to the internet. http (internet) its accessed through port 80 and you can't change that, some applications can change the port they'll use to send info. For example bit torrent. 

Usually security settings block the ports that are not being use, so you must open them and assign them to your application, that is what port forward means.

Go here: [http://portforward.com/routers.htm](http://portforward.com/routers.htm)

Probably your ports are blocked, which client are you using?

---

### Post by uberlube on 2008-02-23
Ya other sites are still fairly good. Its just my bittorrent client.

---

### Post by ruy_lopez on 2008-02-23
It might be that the torrent is experiencing heavy traffic. Try a different torrent.

---

### Post by Diabolis on 2008-02-23
> It might be that the torrent is experiencing heavy traffic. Try a different torrent.

Torrents do not experience heavy traffic, actually the more traffic the faster you'll download. Thats why torrents are fast, they use user bandwidth instead of server bandwidth. So more users equals more bandwidth.

---

### Post by Diabolis on 2008-02-23
If you are using bittorrent, type in terminal:

```
gconf-editor
```
 
and go to:

```
apps/gnome-btdownload/settings
```

there you can change the values of max_port and min_port. Just make sure you assign ports that are open in your router or whatever you use.

---

### Post by uberlube on 2008-02-23
Is there any real way to speed up downloads that you know about or are we at the mercy of the traffic?

---

### Post by ruy_lopez on 2008-02-23
> **Diabolis said:**
> Torrents do not experience heavy traffic, actually the more traffic the faster you'll download. Thats why torrents are fast, they use user bandwidth instead of server bandwidth. So more users equals more bandwidth.

You're right. Maybe his torrent is NOT seeing heavy use.

---

### Post by Diabolis on 2008-02-23
you can configure the values of the bittorrent, just play with them. I've done it and you do get higher speeds, but since users are joining and leaving torrents frequently, you have to change the values again and again. So it is better to leave the defaults, and just make sure your ports are open.

yeah, maybe thats the problem, low seeds = low download speed

uberlube, have you checked how many seeds does the torrent that you are trying to download have? maybe they are not enough

---

### Post by uberlube on 2008-02-23
I am actually using Deluge but yes my incoming is unlimited and outgoing is a 40kb max

---

### Post by uberlube on 2008-02-23
I only choose high seed with low leech. But my origional question is how to make sure the ports are properly open n 'junk

---

