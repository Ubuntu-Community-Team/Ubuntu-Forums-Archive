---
title: "Getting messages from NM &quot;Connection to AP lost&quot;"
date: 2023-06-19
forum: Networking &amp; Wireless
---

### Post by Alex_Filonov on 2023-06-19
This is an issue I started having on my laptop after upgrade to 22.04. Never had this problem on 16.04, 18.04, 20.04. Quite often, wifi reconnects. Sometimes every 2 minutes, sometimes every 30 minutes. In the beginning of every reconnection, I'm getting a message: 

Connection to AP (AP mac address) lost. 

After that, within 3-5 seconds connection is renegotiated and restored, often with a new IP address.
I have a pretty decent signal, bitrate is usually 390 Mb/s with an wifi adapter having max bitrate of 433 Mb/s. 

One of strange messages I receive is this one:

connection_factory_impl.cc(428)] Failed to connect to MCS endpoint with error -106

Any ideas what's happening?

---

### Post by aljames2 on 2023-06-19
You mention you upgraded to 22.04.  Also, that over time you are coming from 16.04.  When was your last fresh install?  I typically only upgrade 1 release before doing a fresh install to the next release.  If your last fresh install was 16.04 or 18.04, you should consider a fresh 22.04.  Others here may offer some suggestions you could otherwise try first.

---

### Post by Alex_Filonov on 2023-06-19
Actually, 22.04 was the fresh install. I upgraded my laptop, replacing HDD with SSD and did a fresh install of 22.04.1 on a blank disk.

---

### Post by Alex_Filonov on 2023-09-15
Closing this thread. Retiring the old laptop, haven't seen such problem with a new one.

---

