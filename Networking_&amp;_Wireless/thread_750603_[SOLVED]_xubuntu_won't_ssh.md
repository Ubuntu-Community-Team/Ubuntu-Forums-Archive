---
title: "[SOLVED] xubuntu won't ssh"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by gishaust on 2008-04-09
Hi everyone

I have a webserver that has ssh server attached. If I use putty on my windows machine I can ssh the webserver fine. but if I try to use Xubuntu from the terminal using the following commands I says the 
```

 Name or service not known

```

I have installed ssh on xubuntu by sudo apt-get install ssh and it installed fine .
In the terminal I have tried
```

sudo ssh bill@192.167.1.300:1000 ( this is an examle).

```

I use to this on my ubuntu 7.04 desktop and could ssh anytime!!!

Has anyone got any ideas on what I might be doing wrong

gishaust

---

### Post by jetsam on 2008-04-09
I think so.  Just a simple syntax thing.  You want
```
ssh -p <port> <user>@<ip_address>
```

So, using your example:
```
ssh -p 1000 bill@192.167.1.300
```

That 300 number in your example ip is impossible, but I'm assuming it's just the example and your real ip doesn't have a quad number over 255.

For whatever reason, ssh parses port numbers differently than, say, firefox.

---

### Post by gishaust on 2008-04-12
thanks it works great

---

