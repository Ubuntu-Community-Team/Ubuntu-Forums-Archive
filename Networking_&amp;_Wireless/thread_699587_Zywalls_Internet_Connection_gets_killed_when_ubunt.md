---
title: "Zywalls Internet Connection gets killed when ubuntu computers download large things"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by kaefert66014235 on 2008-02-17
Okey so this is about my internet connection @ the home of my girlfriend..
I've got a Zyxel Zywall2 which plays router for my network, and many of the clients are winows machines, which dont cause any problems.
When i connect ubuntu hosts, first everything works as it should, they get private ip-adresses assigned and can access the internet in every way. But when i do something that requires large downloads (more than some k) like installing software, or directly downloading something via a browser, it somehow kills the WAN connection of the Zywall. So not the LAN connection from the host concerned but the internet connection for the whole network.

The same phenemon also happens when performing downloads from virtual winxp pc's running in virtualbox on an ubuntu host. So I think from that you can tell that it is unrelated to the used software, but somehow connected to the basic networking of linux / ubuntu.

i cant think of anything that an ubuntu host could send while downloading stuff differently than a windows host - isnt a http-request always a http-request?!

i hope someone has a clue and can help me.

some more facts:
-) i've used differently ubuntu hosts, all running 7.10
-) the same ubuntu hosts dont cause any problem @ my home, with another one of the same router-make (zyxel zywall2) and the same internet provider (inode) - the only difference i see between the 2 sites is that @ my home the internet connection is "entbündelt" = independent from the austrian "Post" = "mail"?

---

