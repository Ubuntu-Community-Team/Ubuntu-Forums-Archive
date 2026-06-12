---
title: "Run Script When Internet Connects"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by sumadartsan on 2007-02-03
I was wondering how I could have a script run each time my laptop connects to a wireless network.  Basically, I would like it to mount a sshdfs location everytime I have connectivity.  However, I can imagine many other good uses to this.

What is the best way to achieve this?  Does anyone know some documentation I can read to get a deeper understading of the networking startup process?

---

### Post by kidders on 2007-02-03
Hi there,

Lots of stuff tends to get done (especially for PPP-based connections) around the time of an interface going up/down. Check out /etc/network for some examples. Depending on what you've installed, there could be quite a few scripts in some of the subdirectories in there.

You should be a little bit cautious about associating complex activities such as mounts with the state of a wireless connection, though. If your signal gets flaky, your script could wind up being re-executed rather a lot. You might end up causing trouble on the server that's hosting your network shares, or making your own machine weird/unresponsive.

---

