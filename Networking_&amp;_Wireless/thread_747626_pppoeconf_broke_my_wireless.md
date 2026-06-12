---
title: "pppoeconf broke my wireless"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by arkros on 2008-04-06
I used pppoeconf to connect to my schools wireless network, it worked fine. I made the mistake of accepting the 'activate on boot' option. And after a reboot, my wireless isn't working anymore. Wired connection works fine.

---

### Post by pseudo-random on 2008-04-06
Are you sure? Wireless networks don't use PPPOE.
It sounds like you used it to connect to a wired DSL connection.

---

### Post by arkros on 2008-04-06
When I used windows, I had to make a pppoe connection to connect to the schools wireless. I had to connect to the access point normally first, and then use the second connection to authenticate. It worked in ubuntu as well, using pppoeconf after I connected to the access point.

No wired dsl.

I'm thinking it's something to do with the activate at boot option in pppoeconf. I didn't intend to select it, but now I can't undo the changes.

---

