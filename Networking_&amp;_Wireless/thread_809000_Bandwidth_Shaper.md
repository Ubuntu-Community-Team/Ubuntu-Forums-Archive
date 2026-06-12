---
title: "Bandwidth Shaper"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by longinustorwaldzki on 2008-05-27
Hello there Ubuntu Community!

I'm running Ubuntu Server 8.4 on my server that routes more than 50 machins in my network to the internet.


For a while now I was looking for a way to manage bandwidth in my network. I found Master Shaper which didn't really want to run on ubuntu (I tried it in debian and works fine) What I want to gain is ability to monitor and shape the bandwidth for each machine in my network on all necessary ports.

any help would be appreciated
regards!

---

### Post by SpaceTeddy on 2008-05-28
this [[COLOR="Blue"]article[/COLOR]]("http://www.linux.com/base/ldp/howto/Traffic-Control-HOWTO/index.htmlt") explain on how to use tc (traffic control). I think that should get you started. 
tc is installed by default on ubuntu (or, if not, it's in the paket iproute2, i think...)

---

