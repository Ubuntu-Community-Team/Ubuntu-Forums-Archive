---
title: "mounting shares based on network"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by zordid on 2008-11-09
I would like a script to mount shares based on the network my computer connects to. I was thinking about something like this:
```

case NETWORK
  network1:
    mount shared on network1

  network2:
    mount shared on network2

  network3:
    start vpn
    mount shared on network3

```

How can I from a script see which network I am connected to and how/where do I execute the script after the computer has connected to a network?

---

