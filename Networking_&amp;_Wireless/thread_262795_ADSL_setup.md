---
title: "ADSL setup"
date: 2006-09-22
forum: Networking &amp; Wireless
---

### Post by src2206 on 2006-09-22
Hi,
I connect to internet via my onboard LAN card using an ADSL modem. I need to connect through the ADSL using specific username and password, ie, its not an alltime on connection.
Could someone please help me how to set up this connection?
I'm using Ubuntu 6.06.01.

Thank you.

---

### Post by drunken-wallaby on 2006-09-22
Hi.

You can setup your ADSL connection via ```
sudo pppoeconf
```
You can start the connection with ```
pon dsl-provider
``` and stop it with ```
poff dsl-provider
```

Bernhard

---

### Post by src2206 on 2006-09-22
Thank you very much.
I'll let you know about the result in my next post.
BTW could you provide me a link to all the commands available in Ubuntu and a essential downloads page?
Thanks again.

---

### Post by src2206 on 2006-09-23
Thanks, my Ubuntu connection is up and running.:D 
Could anyone please help me with my second request in my last post?:-({|= [-o<

---

