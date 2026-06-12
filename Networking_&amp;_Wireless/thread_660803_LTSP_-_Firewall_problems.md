---
title: "LTSP - Firewall problems"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by JoeGregory on 2008-01-07
Hi,

Here is my set-up.

Dell AMD64 with two NICS

 - Wireless NIC for connecting to broadband router
 - wired NIC for ltsp network

Running Gutsy and LTSP 5.0

Everything working basically ok but I have the following issue which I can't solve myself.

I would like to run the server as just that, a headless server. Basically I would like anyone, including my wife, to be able to switch on the server, without logging into the server directly and then start a client. However, at the moment I have to log-in and do a "sudo ....network restart" before the clients will boot. I believe this is because Firestarter doesn't run properly at boot-up because the wireless i/f is down. Does anybody know the cause of this?

I have set up firestarter correctly as with firestarter running the client will boot. But only after the network restart.

Any help or advice would be appreciated.

Thanks

---

