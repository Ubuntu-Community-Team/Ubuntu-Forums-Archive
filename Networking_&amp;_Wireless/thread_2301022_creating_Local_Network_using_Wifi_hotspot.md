---
title: "creating Local Network using Wifi hotspot"
date: 2015-10-30
forum: Networking &amp; Wireless
---

### Post by samuel40 on 2015-10-30
I want to periodically share files to set of Local users.
Currently these files are uploaded on internet site and Users download these files on smartphone. The Download consumes mobile data.

I was thinking of a way where in these files uploaded on one of a ubuntu desktop. Creat a wifi hotspot service on this desktop where in public could able to connect freely.
The files are stored in desktop's webserver's folder. All smartphone users have to connect the webserver through  smartphone browser and download the file through http request.

Could someone guide me how to do this. Also let me know if there are other way of solving this problem.

Appreciate your prompt reply.
Thanks.

---

### Post by ian-weisser on 2015-10-30
A 'hotspot' implies that you want to share a single internet connection among several. Otherwise known as [internet connection sharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing").

However, your description seems more like an ad-hoc network. You simply want to share local files, not internet access.
Simple enough - Network Manager already does this.
1) Click on the NM icon, select 'Create A New Wi-Fi Network'. Fill in the blanks (network name, security, etc).
2) After creating the network, connect to it.
3) Start your web server
4) Have your friends connect to it.

If you are accessing the internet using Wi-Fi, this will disconnect you. Most wireless cards and dongles can only handle a single network at a time.

Android devices with stock firmware generally cannot connect to ad-hoc networks, due to a decision by Google. For them, you need an *access point*, which only a few wireless cards and dongles can do properly. *ad-hoc* and *access point* are two different types of wireless network, though the differences are not apparent to users. Network Manager will happily create an access point...if your hardware supports it.

---

