---
title: "SSL over OpenVPN resource expense"
date: 2013-10-02
forum: Networking &amp; Wireless
---

### Post by Starfleet_Engineer on 2013-10-02
I want to setup a SSL over OpenVPN connection to my VPN service. Before I do, I want to know what the impact on my system's resources would be.  I know how to test using ```
openssl speed -evp aes-256-cbc
```  Is there a combination command I can run that will simulate piping SSL through aes-256-cbc?

---

### Post by TheFu on 2013-10-02
The number of connections, the amount of data transferred, the capabilities of your CPU, your internet connection, the OpenVPN server settings, key length, number of users, server performance and latency all go into "system resource" questions.  I could lie and say almost nothing or 50% - but really there is no way to know.

Set it up and measure it is the only sane answer any one can provide. Your situation is different from ours.

If you are an engineer, you know this already. ;)

All the simulations in the world won't mean anything until you test it on the systems to be used. Even then, factors outside your control **will** impact performance.  On a i386, the impacts might matter, on a Core i7, it probably doesn't matter at all.

If you really care about system resource impact, why not run OpenVPN on the router instead?  dd-wrt, pfSense and others will do this depending on your router hardware.

---

