---
title: "Dog-slow SFTP transfers"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by kartik_vad on 2008-10-14
When I try to copy files from my Macbook Pro to my Ubuntu 8.04 box over SFTP, I got a speed of ~1Mbps yesterday, and only ~100KBps today. This is over a 100 MBps wired LAN. The Mac client is Cyberduck; restarting it did not help; nor did using scp from the console, or scp in the reverse direction from the Ubuntu machine. 'top' shows that both machines' CPUs are > 80% free, so that's not the bottleneck, and neither is the network. I saw some complaints about gvfs, but scp is affected as well. What is going wrong, and how do I fix it?

---

