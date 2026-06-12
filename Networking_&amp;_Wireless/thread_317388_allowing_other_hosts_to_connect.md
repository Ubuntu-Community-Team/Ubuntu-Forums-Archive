---
title: "allowing other hosts to connect"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by bflight1021 on 2006-12-12
Good morning!

I've just switched to ubuntu from opensuse, and i've run into a bit of a snag. on my prior setup, i had been using an ssh tunnel to allow myself and a co-worker access to AIM - however, since switching to ubuntu i cannot seem to allow my co-worker to connect - however i have no issues locally. 

Here is the command i use:

ssh -C -D1080 <user>@<host>

then on the aim/gaim client side, i simply configure the app to use localhost:1080 (or in my co-worker's case <ip>:1080) as a SOCKS4 server.

As i said before this works fine for me locally, but my co-worker cannot connect to the tunnel (we had been doing this for ages with opensuse).

So logically i hit up the ubuntu wiki thinking there may be a firewall of sorts pre-installed, however the docs lead me to think the firewall is a package that's added later. 

Anyway, thanks in advance for any help!

---

### Post by bflight1021 on 2006-12-12
bump - anyone?

---

### Post by bflight1021 on 2006-12-12
one last bump - any help would be appreciated!

---

### Post by Iowan on 2006-12-13
[http://doc.gwos.org/index.php/BreezyFreeNX]("http://doc.gwos.org/index.php/BreezyFreeNX")
I found this one whilst searching for "ssh tunnel", but it's probably not what you were looking for.

---

