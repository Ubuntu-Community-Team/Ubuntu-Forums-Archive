---
title: "Setting up a Proxy Server"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by prodonjs on 2007-12-04
For a course requirement, I set up an FTP server using Ubuntu Server 7.10 running inside a VMWare virtual machine. My goal for this project was to build a lightweight server inside a VM that could run on a host machine inside my private network at home, that I would be able to SSH to, start torrent downloads, and then be able to later access those downloads via FTP from my computer here at college. The reason of course was because like most universities, our school blocks access to torrent clients (despite the fact that they are legitamite forms of file sharing with reasonable uses, particularly for computing students). 

Anyways, I just realized that I might even have a slicker solution to my predicament. I would now like to have my Ubuntu Server act as a proxy server so that I can establish torrent connections through it and use my local machine here to download and share torrents just as if I was outside of our university firewall. 

Now I don't know very much about proxy servers except that there are simple web proxies, and SOCKS proxies and as far as I understand, the latter can be configured to allow communication across more than just the HTTP protocol. Beyond that though, I'm really inexperienced and I would like to be pointed into the direction of some reasonable tutorials that would help me get a simple proxy server up and running.

I greatly appreciate any help.

---

### Post by Friek on 2007-12-06
Take a look at [squid](http://www.squid-cache.org/). There are probably a zillion tutorials online on how to set it up ;)

---

### Post by prodonjs on 2007-12-11
I looked into Squid and it seems to be much more full-featured than I need. I really don't need the use of a caching proxy server within the LAN that it will be running on. I am more concerned with having a proxy server that I can route through for use with a BitTorrent client.

I would basically like the server to be a transparent node that I will send all BitTorrent protocol messages through, and that will be able to send them back to me (I'm assuming that it can do so through HTTP messages that would pass through the firewall at my university?). I really haven't found any useful information pertaining to the problem that I have. I am not concerned with gaining web access via the proxy, but I want to be able to use the proxy to handle the torrent connections that my university network will not allow.

---

### Post by xur17 on 2007-12-12
Here is a tutorial that you can use to tunnel connections to your home:

[http://www.revsys.com/writings/quicktips/ssh-tunnel.html](http://www.revsys.com/writings/quicktips/ssh-tunnel.html)

---

