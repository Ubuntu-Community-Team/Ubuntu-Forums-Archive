---
title: "[SOLVED] Can't ping external addresses"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by abruegl on 2007-08-06
Strange problem...

After our system admins at work upgraded our domain controller, I can no longer ping any external addresses, like this:

abruegl@abruegl-desktop:/etc/network$ ping [www.cnn.com](www.cnn.com)
PING [www.cnn.com](www.cnn.com) (64.236.16.20) 56(84) bytes of data.

It just sits there forever. The strange thing is I can use Firefox without problem. Any idea on where I might fix this?

Thanks so much!

---

### Post by tgm4883 on 2007-08-06
> **abruegl said:**
> Strange problem...

After our system admins at work upgraded our domain controller, I can no longer ping any external addresses, like this:

abruegl@abruegl-desktop:/etc/network$ ping [www.cnn.com](www.cnn.com)
PING [www.cnn.com](www.cnn.com) (64.236.16.20) 56(84) bytes of data.

It just sits there forever. The strange thing is I can use Firefox without problem. Any idea on where I might fix this?

Thanks so much!

maybe they blocked ping?

---

### Post by abruegl on 2007-08-06
Looks like it's not an Ubuntu problem, but something the sys admins messed up with the network. Seems like about half of all sites can be pinged and others can't - same deal on Windows.

Sorry for posting! #-o

---

### Post by tgm4883 on 2007-08-06
no prob, can you get your thread removed or at least mark it as resolved?

Thanks

---

