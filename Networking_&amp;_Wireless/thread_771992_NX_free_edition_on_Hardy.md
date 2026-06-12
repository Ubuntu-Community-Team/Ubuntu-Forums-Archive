---
title: "NX free edition on Hardy"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by Nick Payne on 2008-04-28
I have been running the Nomachine NX free edition on 7.10 for quite a while with no problem. I just downloaded 8.04 i386 release and did a fresh install onto a new partition, then installed the current NX from [http://www.nomachine.com/download-package.php?Prod_Id=5]("http://www.nomachine.com/download-package.php?Prod_Id=5").

I also installed the current NX client for Windows, but when I try to connect from the Windows machine, the client starts to connect but then puts up an error dialog saying > DSA key is corrupted or has been protected with a passphrase

I had a look at /usr/NX/etc/keys/node.localhost.id_dsa but it looks as a key should:

```
-----BEGIN DSA PRIVATE KEY-----
MIIBuwIBAAKBgQD+fwhOoqOJHiRvL3zWLeG9o9C1Gk2fdAi1T4julWXSxXD3HrLZ
zydH7ngGkEMJqtSS4YU9jcFJF70+JuJISDPLXISYjkdzMilyprRQ2PstjYr1h4Rq
ccKn/vpHtUgFY9h7pjcVriL9KJorZR7/vH9c8kJ/DTcHAUD1MB1211BovQIVAK7o
lVhOwepA7ulZmJEqZfVCQpmnAoGAdlkU1Y6CuzWBRZK9ep+Brb6Ik0eWSVkRfUqT
RXIKERk+lzZAtItqE0iI5vPoT0klvId/gMLO/eBBBMsnx8dmCwqnpVJnjklOiyq/
6Mk8f9Yr0JiLUJneDolBLHEUfFJcEWA7O1g0xY/GNvRqq6EI69/1P5of9ABGByfw
9QRBeG4CgYEAi63d7pOQojP2BIMKiRfAMwMUa0wfcqWxiDYmSuoRklnKaTtmQUOY
DOmviQmMUSduiABWkYhZCdo6hcTP/pFuRWF3/nwBJoUoaJxFFaBWC9U0I2mN9EI0
iMBhEzLtAhwPEEvrxDR75s0kl6D3D9VQDvg1FONPdMJx+6KGn+FKEQMCFEu3r9I7
Aqfi5eF7d+ZqZOTFMEJW
-----END DSA PRIVATE KEY-----
```
I did a bit of googling but didn't find anything pointing me in the direction of a fix.

Nick

---

### Post by Sawyer_ on 2008-05-28
I have this same issue and I've been struggling with it for a few hours trying to reset the keys server and client side without a solution.

---

### Post by lsutiger on 2008-11-23
Same problem...any solution?

---

### Post by cocotu on 2008-12-08
you should try:
[http://www.nomachine.com/documentation/admin-guide.php](http://www.nomachine.com/documentation/admin-guide.php)
section:
4.4. Replacing the Default SSH Key-Pair with Keys Generated for Your Server

---

