---
title: "How are multiple connections handled?"
date: 2015-10-13
forum: Networking &amp; Wireless
---

### Post by tristan16 on 2015-10-13
Basically, I can connect my computer to the internet in 3 ways: Wi-Fi, Ethernet, and my smartphone via Bluetooth. When I have more than one connection, how does Ubuntu decide which to use? Does it try to balance network traffic between the connections, or does it just use the one that was connected first and use any other connections as fallback? I'd also like to know if there was a way to combine internet speed across connections, similar to the Speedify program on Windows.

---

### Post by TheFu on 2015-10-13
Ubuntu is linux.
This is how Linux does it: [http://www.tldp.org/HOWTO/Adv-Routing-HOWTO/](http://www.tldp.org/HOWTO/Adv-Routing-HOWTO/)

The overall ideas are the same as Unix.

---

### Post by tristan16 on 2015-10-13
> **TheFu said:**
> Ubuntu is linux.
This is how Linux does it: [http://www.tldp.org/HOWTO/Adv-Routing-HOWTO/](http://www.tldp.org/HOWTO/Adv-Routing-HOWTO/)

The overall ideas are the same as Unix.

Wow, thanks! Lots of reading. This page talks about setting up rules as if the computer were the router with other devices connecting to it. Would routing rules like this work on the local machine as well?

---

### Post by TheFu on 2015-10-14
> **tristan16 said:**
> Would routing rules like this work on the local machine as well?

Don't know why they wouldn't.
Interfaces are prioritized by the "metric" number if both interfaces are on the same network. Routing is how different networks are connected. 

BTW, to use this stuff some minimal amount of networking knowledge is necessary.

---

