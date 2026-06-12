---
title: "pptp error &quot;no device specified and stdin is not a tty&quot;"
date: 2014-08-12
forum: Networking &amp; Wireless
---

### Post by TCSnyder on 2014-08-12
I am setting up a PPTP vpn and I can connect locally to the IP address sucessfully. 

When I try to connect over the internet I get the following error on the server.
```
Aug 12 23:10:28 myserver pptpd[3363]: CTRL: Client **.**.**.120 control connection started
Aug 12 23:10:29 myserver pptpd[3363]: CTRL: Starting call (launching pppd, opening GRE)
Aug 12 23:10:29 myserver pptpd[3363]: CTRL: Reaping child PPP[3364]
Aug 12 23:10:29 myserver pppd[3364]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Aug 12 23:10:29 myserver pppd[3364]: no device specified and stdin is not a tty
Aug 12 23:10:29 myserver pptpd[3363]: CTRL: Client **.**.**.120 control connection finished

```

The ports are forwarded correctly, since it is reaching the server, but I cannot findany information online.

pptp version 1.7.2
Ubuntu 14.04 ( server and client )

Thanks for your help!

---

### Post by TCSnyder on 2014-08-12
It looks like I may have solved the issue. It does not like to connect over the web back to my same IP address. I tried from a different network and it seems to work fine

---

