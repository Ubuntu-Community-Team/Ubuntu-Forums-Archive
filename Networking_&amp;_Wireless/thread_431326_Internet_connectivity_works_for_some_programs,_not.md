---
title: "Internet connectivity works for some programs, not for others"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by vedace on 2007-05-02
Quite simply, I can browse websites just fine in firefox, and I can use gaim (er, pidgin) normally, but other programs give me trouble; irssi spits out "Unable to connect server [servername] port 6667 [Connection refused]", and Google Earth can't connect to the image server.  I have a sneaking suspicion that this could have something to do with the fact that I played around with tor and privoxy at some point, but neither process is running.  Outgoing ping, traceroute, and nmap all work just fine.  nmapping localhost tells me that 22 is open for ssh and 631 for ipp.  System > Preferences > Network Proxy has "direct internet connection" set.  

Any ideas?  I'm running feisty, by the way.

EDIT: irssi wasn't working because the server was down, so that's all fine and good.  This question therefore boils down to: why isn't google earth working?  It tells me:

```
Google Earth detected an error whiel trying to authenticate
Please check the following:
- your network connection (can you get to www.google.com?)
- your firewall settings
[are tou blocking /usr/local/bin/google-earth/googleearth-bin?)

Error code: 29

```

---

