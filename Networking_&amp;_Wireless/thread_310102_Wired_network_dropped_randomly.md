---
title: "Wired network dropped randomly"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by johneboy on 2006-11-30
Hi All,

I am running Ubuntu 6.10 on a Sony Vaio VGN-SZ2XP.  On installation everything was picked up fine, even the wireless networking and bluetooth.

Problem is my wired network connection (eth0) randomly drops and the only way I can bring it back up is to issue the following commands:

```
sudo ipdown eth0
sudo ifup eth0
```

There seems to be no pattern to when the connection is dropped and network manager doesn't seem to pick up the fact that the connection has disappeared, until the ```
ifdown
``` is issued. I have booted into windows to see if the problem occurs then but it appears stable.

This is really annoying as I use my laptop for work and there is no wireless access point in the office.

Has anyone else noticed this and/or does anyone have a solution/suggestion?

Many thanks

Regards

John

---

### Post by divague on 2006-11-30
I had a similar problem, someone advised me to use opendns [http://www.opendns.com](http://www.opendns.com) ,and that fixed my problem.

---

### Post by johneboy on 2006-12-04
Ok,

after some investigation it would appear that the issue is caused when using an NTLM authenticated proxy server.

I configured my proxy server via the Menu "System/Preferences/Network Proxy" and specified the authentication credentials.

If it helps I was using the same proxy for all protocols.

Moving to an unauthenticated proxy allows me to work around the problem.

Regards

John

---

