---
title: "DNS Resolution, I Can Ping but cannot resolve"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by tig4 on 2008-05-23
Hey All, /me tips hat

So on my network we have static ip configurations. I have manually entered my ip and can ping everything internally. I set my nameservers and can also ping them (external DNS servers) however, I cannot seem to resolve any hostnames, i.e. google.com, ubuntu.com, digg.com, etc.

Any ideas? BTW, I'm using two network cards if that makes a difference.

Thanks,

Tig

---

### Post by MaindotC on 2008-05-23
Are your nameservers from an ISP or did you set them up yourself?  If you set them up yourself I believe you need to comment the "{allow-query}" line.  It should be set to "local" which means it will only resolve addresses on its own machine and not allow any outside queries.

---

### Post by mapes12 on 2008-05-23
Please could you post the output from:

```
cat /etc/resolv.conf
```

---

### Post by tig4 on 2008-05-23
No they are the ISP DNS Servers. That's the wierd thing

---

### Post by tig4 on 2008-05-23
for whatever reason, i changed nothing, the dns now resolves... weird. Thanks for the help guys. :)

---

### Post by MaindotC on 2008-05-23
I notice in Ubuntu that when I change the network configuration it kind of takes a couple minutes to inititate.  Sometimes I try 
```

/etc/init.d/networking restart

```
but it still takes a minute or two to start working.  Those are valid DNS servers from comcast in Denver so I'm glad everything is working for you.

---

### Post by mapes12 on 2008-05-23
Great news!

Would you be kind enough to mark the thread as SOLVED please.

---

