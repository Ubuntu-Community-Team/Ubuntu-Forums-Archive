---
title: "Network adapter problems (wired and wireless)"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by doctorbighands on 2009-02-10
The machine is an iBook G4 running Ubuntu 7.10.

Problem 1: I have no wired connection. I used a mini install just now to get Ubuntu installed, so I know it works. I don't know why Gutsy doesn't recognize it. A "iwconfig" command reveals "no wireless extensions" where the wired NIC should be.

Problem 2: The wireless connection is a Broadcom 43xx. According to the Restricted Drivers Manager, I got the driver installed properly and it's "in use" but network manager doesn't see it, so I can't connect to anything. iwconfig can see it, though.

Any help is much appreciated. Thank you!

---

### Post by doctorbighands on 2009-02-10
Ok, so, after further investigation, it seems the problem with the wired connection is the network manager itself. If I go to "manual configuration," I can enable the wired connection, and now I'm online.

I still have no connectivity with the wireless connection, even after configuring it in network manager. That problem still remains to be solved, and I'd love some ideas!

As for getting other things to cooperate (I just realized that the sound isn't working either), I'm trying an upgrade to 8.04. Maybe that'll solve some things.

---

