---
title: "How to properly blacklist skge?"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by lingenfr on 2008-09-14
I am trying to get my Linksys EG1032 gigabit ethernet card working. I tried working with the default skge that came with mythbuntu, but no joy. The sk98lin driver looked pretty old and it seemed that there were a number of problems with that as well. I have seen that folks are having some success with ndiswrapper which I am familiar with, so I tried that. However in order to make that work, I need to blacklist skge (I think). I added 'blacklist skge' to the end of my /etc/modprobe.d/blacklist file, but it is still loading when the machine boots. What else do I need to do?

---

