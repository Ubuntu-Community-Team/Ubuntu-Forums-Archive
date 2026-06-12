---
title: "Connects to Wifi but No Internet: DNS issue?"
date: 2024-10-10
forum: Networking &amp; Wireless
---

### Post by hJrBzw3 on 2024-10-10
In an upgrade from Jammy Jellyfish to Noble Numbat, I lost the ability to connect to the Internet without issue.

My wireless card still works and connects to Wifi networks as before. But now something is happening that prevents it from going online. I've managed to Macgyver a solution thanks to a solution I got to YouTube: running "echo nameserver 8.8.8.8" | sudo tee /etc/resolv.conf > /dev/null" nudges something and then I can get online, so I guess it has something to do with my DNS resolver?

---

