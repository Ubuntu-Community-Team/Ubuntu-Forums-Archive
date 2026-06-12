---
title: "Not able to open a port for Transmission"
date: 2013-11-09
forum: Networking &amp; Wireless
---

### Post by emanuele-cavallaro2 on 2013-11-09
Transmission stopped workin on my computer. Every tracker goes timeout while trying to connect.
In Transmission -> Preferences -> Network clicking the Test Port button the port (51415) results closed.

I tried opening it with ufw and issuing ```
ufw status
``` it says:
```

Status: active

To                         Action      From
--                         ------      ----
51415                      ALLOW       Anywhere
51415                      ALLOW       Anywhere (v6)

```

But for transmission the port results still closed.
Help me, please.

---

### Post by Toz on 2013-11-09
Hello and welcome to the forums.

How are you connected to the internet? If its through some sort of router, you'll need to configure the router to port-forward 51415 to your computer.

---

### Post by emanuele-cavallaro2 on 2013-11-09
I am connected with a wifi router.

Anyway... Now it works again but I do not know why.
I did not do anything and the port results always closed in Transmission.

Thanks

---

### Post by Toz on 2013-11-09
To make a direct port connection through a (in your case wifi) router there are two things that need to happen:

1. The port needs to be open and listening on the computer you are using. If a firewall was enabled, then the port needs to be allowed through (this you have already done with ufw)

2. The router that connects your computer to the internet needs to be setup to forward that port to your computer. Look at the router documentation for information on how this is done.

And in the case of bittorrent, some ISPs block torrent traffic. This may also affect your ability to use the bittorrent protocol.

---

