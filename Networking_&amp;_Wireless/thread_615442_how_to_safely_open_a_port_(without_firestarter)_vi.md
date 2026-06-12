---
title: "how to safely open a port (without firestarter) via iptables"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by takayuki on 2007-11-17
Hi,

I'd like to open port 22 so i can ssh into my linux box from whereever.  I've installed openssh server and can ssh between my mac and linux boxes behind the dsl router, but from the "outside" on the net, I can't ssh in.  I get the old "connection refused" error.

I checked and sure enough port 22 is closed.

I'm running moblock and heard that it conflicts with firestarter.

So how can i safely open up port 22?  configuring the ip tables seems daunting.

any help greatly appreciated.

regards,

takayuki

---

### Post by 5-HT on 2007-11-17
You'll need to open up 22 on the router, it's nothing to do with the box or iptables as you can easily connect on the lan. As to safely though...
cheers,

---

