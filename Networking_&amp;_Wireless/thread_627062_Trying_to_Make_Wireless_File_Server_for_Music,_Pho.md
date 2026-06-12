---
title: "Trying to Make Wireless File Server for Music, Photos, Etc. Need help."
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by jrdemasi on 2007-11-29
Hey, New to the forums, but Great community you have here!  I was recently trying to make a file server on an old windows box and I got fed up with having to restart everytime there was a windows update.  SO - I decided to try it out with Ubuntu.  I don't have a problem setting up the server normally, however, I'm not sure how it works to wirelessly access the server.  

Any Help Much Apprciated,

---

### Post by uclalinux on 2007-12-01
I am not sure what you mean wireless, but if you mean over a network (wired or wireless) then  I think you want a samba server, this will allow you to have shared network files where music, photos. movies etc. can be stored. the files can be accessed as if they were on your remote computer, even though they are on your server. 

Here are a few web sites for how to set up samba, plus there are tons of howto's on the web. 

[http://www.samba.netfirms.com/](http://www.samba.netfirms.com/)
[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)

here is my smb.conf file, mine is very basic but its all I need
```

workgroup = home
netbios = samba
encrypt passwords = yes
wins support = yes

[home]
read only = no
browesable = no

[uclalinux]
path = /home/uclalinux/
browseable  = yes
write list = uclalinux
read only = no
```

---

### Post by jrdemasi on 2007-12-01
Thanks a bunch.  That's at least a good start.  If I hit any speedbumps along the way I'll let you know.

---

### Post by uclalinux on 2007-12-03
if you need help, please google the question for about 10 min's if you can't find an awnser then just email, me at [email]uclalinux@gmail.com[/email]

---

### Post by netztier on 2007-12-03
> **jrdemasi said:**
> Hey, New to the forums, but Great community you have here!  I was recently trying to make a file server on an old windows box and I got fed up with having to restart everytime there was a windows update.  SO - I decided to try it out with Ubuntu.  I don't have a problem setting up the server normally, however, I'm not sure how it works to wirelessly access the server.  

Any Help Much Apprciated,

Be careful with "wireless" and servers. I generally discourage connecting a server via Wireless. See also this post (and thread):

[http://ubuntuforums.org/showpost.php?p=3319772&postcount=16](http://ubuntuforums.org/showpost.php?p=3319772&postcount=16)

(it's about running NFS on a server connected va Wireless, but the "bandwith race" problem will occur regardless of the file sharing protocol being used).

I suggest hooking the server to the wired part of the LAN, add a WiFi AccessPoint device to it. Most common "Wireless broadband routers" integrate a router, a switch (for the wired LAN) and a WiFi AccessPoint in one box, so with some luck, you won't need ot buy extra equipment.

The key step is ot make sure that traffic from server to client and back is "transit" traffic for the AccessPoint from the wired to the wireless part of the network (or the other way). 

Wireless-to-Wireless traffic is more difficult to handle for a single AP and suffers the "race for wireless bandwith" problem in a way that's even worse than it was back in the days of 10Mbit/s half duplex hubs.

Since data packets won't travel from server to client directly but in two legs from server to AP and from AP to client, each data packet has to use the wireless "medium" twice, which just plain halves the bandwith capacity of your WiFi network. So from the real-world 20-25MBps a 802.11g (54Mbps) can offer, your not going to see much more than half for a single server-to-client communicaton if both server and client are connected to the same AP.

In a nutshell: run the server wired, let only the clients use wireless.

regards

Marc

---

### Post by jrdemasi on 2008-01-20
Just an update to everyone, I got a Samba server working beautifully, Any questions i encourage you to ask on this forum because I hit many speedbumps but found my way around.

---

