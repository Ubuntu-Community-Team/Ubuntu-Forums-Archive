---
title: "Connecting Empathy / Broadcast through Tor help"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by C4U53 on 2010-07-18
I'm trying to route Broadcast and Empathy through the tor proxy. There is no option like in most of my programs, so I tried going to:

System>Preferences>Network Proxy and setting all the tor proxy info there and applying system wide.

I just don't think this is the right way, Though I'm connected to these apps I really don't think they are being routed through tor.

To me it seems Network Proxy is more for those trying to connect to the Internet through a proxy at work or something. Perhaps I'm wrong about this.

also I noticed in the ignore host list of Network Proxy localhost *.host etc were on the list, this leads me to believe 127.0.0.1 with port 9001 (for http 9050 for socks ) is being ignored and its just using the direct connection.

Any help is appreciated!

---

### Post by C4U53 on 2010-07-18
Please help? =( - Just as a note I've scoured the Internet or at least tried and came up with years old post / not applying to my situation or rather tor directly. 

Again, any information is appreciated! Thanks!

---

### Post by mushroomblue on 2010-08-19
I have "torify empathy" added to my startup. I log in, and empathy is automatically routing over Tor.

if it doesn't have socks5 support by default, torify is your friend.

---

### Post by pedi0022003 on 2010-12-23
I have the same problem.
I use Toonel.jar program and I've applied the System-Wide settings but still nothing happens.
Is this a bug or am I missing something?

---

### Post by JoLiSh on 2011-08-08
> **mushroomblue said:**
> I have "torify empathy" added to my startup. I log in, and empathy is automatically routing over Tor.

if it doesn't have socks5 support by default, torify is your friend.

Hi, Can you tell me how to Torify Empathy??
Thanks!

---

