---
title: "SSH Desktop Connection"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by tufcamman on 2008-03-19
Hi everyone, I an running several linux boxes and have a question about SSH.

I installed and set up my server OS to allow SSH connections and that works great, I was just wondering if I could configure my standard Feisty desktop to allow inbound SSH connections so I can open a terminal on my desktop when I'm on the road.  Thanks a ton!

---

### Post by phiphedog on 2008-03-19
Yeah of course. You just need to install ssh server on your feisty desktop and then make sure you forward the ssh port (22) from your router to the machine you wish to access. Then when you ssh to your WAN IP address it will forward the connection to the LAN IP address of your feisty machine.

---

