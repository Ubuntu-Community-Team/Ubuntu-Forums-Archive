---
title: "with sssd and active directory based login, offline/disconnected login fails"
date: 2023-08-04
forum: Networking &amp; Wireless
---

### Post by wuesten-fuchs on 2023-08-04
Hi, I'm out of ideas ... :-(

We have a couple of PC with Ubuntu 22.04, configured to login the user against active directory with SSSD.
As far as I can see, I have correctly configured that the user can log in offline/disconnected (e.g. at home or when traveling) without connection to any DC once the user had logged in successfully while in the network.
This has worked before but after updating Ubuntu a few months ago it stopped working. Since then I am searching for a solution to the problem but can't find one.
In all the logs that sssd produces I can only see that "login failed" and that it cannot reach any DC (which is expected - offline).

What can I do to debug this? Are there any known issues about this? Does anyone of you have an idea what I could do?

---

