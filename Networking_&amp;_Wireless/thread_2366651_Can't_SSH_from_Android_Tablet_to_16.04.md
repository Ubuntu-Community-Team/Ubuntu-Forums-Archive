---
title: "Can't SSH from Android Tablet to 16.04"
date: 2017-07-20
forum: Networking &amp; Wireless
---

### Post by CosmicFlux on 2017-07-20
Hi Guys,

I'm having trouble starting an SSH session from my Android tablet to my main system, running 16.04. So far I've tried:

Set up SSH and have it listening for connections.
Connecting to SSH using the IP address of the main system on port 22 & 2222.
Set up both password authentication (didn't work) and tried generating a public RSA key (didn't work)

I can connect to my phone using my tablet through SSH and also to my tablet using my phone, but I can't use either my phone or tablet to connect to the main system.

I use a VPN to connect the main system to the outside world, but I disabled it to try and establish a connection and still nothing.

What am I not doing? I think Ive spent so much time on this I maybe can't see the wood for the trees!


CF


**EDIT:** Solved! I needed to add my user account to the config file. Schoolboy error. Hate to see it!

---

### Post by TheFu on 2017-07-20
Great that you solved it.

Please use the 'thread tools' to mark this thread as solved to help others in the community.

---

