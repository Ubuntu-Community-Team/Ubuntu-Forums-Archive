---
title: "Networking Issue"
date: 2024-03-19
forum: Networking &amp; Wireless
---

### Post by bmccartney2004 on 2024-03-19
I'm new to Ubuntu so please bare with me. I'll try to explain my situation and hopefully it makes sense! 

I have a local device that has xml data for sensors. My Ubuntu 22.04 has no trouble viewing the the xml data for 10 minutes after a restart. After 10 minutes, the data never fully downloads. But other android and windows devices on the network have no trouble pulling the data at the same time. Is there any settings that would explain this behavior or could you point me in a direction to try to figure it out?

More specifically, I am running telegraf and influxdb. Telegraf is giving me a context deadline exceeded (Client.Timeout exceeded while awaiting headers) but it does the exact same thing if I use curl or a browser. The data partially loads and then stops midway as it times out. But it doesn't do that on any other devices so I have to image it's something going on with Ubunutu. I have no other issues accessing the local network or internet that I'm aware of. 

If you need me to check something, please be as specific as possible because Linux is not my native OS. Thanks!

---

