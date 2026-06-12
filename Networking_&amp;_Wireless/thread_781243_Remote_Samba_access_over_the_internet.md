---
title: "Remote Samba access over the internet"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by fidodo on 2008-05-04
I'm trying to access Samba over an internet connection. I have it working over a local area network but I can't figure out how to access it remotely from a windows machine on a different network. I'm not sure if it's configured for this, or how to connect to it through windows network connections.

---

### Post by SpaceTeddy on 2008-05-04
the samba name resolver only works on local subnets (it utilizes local subnet broadcasts). This means, as soon as you have a router somewhere between you and the destination, the name resoltuon protocoll **does not work anymore**. Also, as far as i know, windows does not fall back on "normal" dns queries when searching for shares. Effectily meaning, even if you have a hostname setup for your samba server, i could not be used.

There are two ways around this...

1.) you use the IP to connect directly to the machine. pressing the start button, going on run and typing in ```
\\IP
``` where IP is the address of the samba server. This way, windows will NOT try to resolve through it's only nameing mechanism, but use the IP instead. This should connect you to the server

2.) you have to use a wins server that you client knows about. A wins server stores all shares of all computers that register to it. Since i a WINS can be specified as an IP or a real hostname (via DNS), it is possible for clients to ask WINS server outside of their subnet to provide information about all servers/clients that propagate their shares to it. This way, you can use the "normal" name again...

hope it helps :)

PS: i personally would never connect a samba directly to the internet, i would always tunnel it over something else... but that is me.

---

