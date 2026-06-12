---
title: "Ufw to block port 80"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by karthick87 on 2010-10-07
I have blockedport 80 in ufw but still i can browse all sites..

```
karthick@Ubuntu-desktop:~$ sudo ufw deny http
Rule added

``````

karthick@Ubuntu-desktop:~$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
80/tcp                     DENY        Anywhere
```How to block the port..?

---

### Post by Neezer on 2010-10-07
I think you just blocked incoming requests on port 80...basically you can't run a webserver with those settings...but I don't think ufw blocks outgoing traffic...

---

### Post by QLee on 2010-10-07
> **getyourkarthick said:**
> I have blockedport 80 in ufw but still i can browse all sites..

```
karthick@Ubuntu-desktop:~$ sudo ufw deny http
Rule added

``````

karthick@Ubuntu-desktop:~$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
80/tcp                     DENY        Anywhere
```How to block the port..?
Unplug from the Internet will very effectively stop you from browsing any sites.

What is it that you are trying to accomplish?

---

### Post by tbohaning on 2010-10-07
I think that the rule you added is denying the inbound traffic.

Try this:     ufw deny out to any port 80

It denies all outbound traffic from this machine to any remote port 80.

---

### Post by karthick87 on 2010-10-07
> **tbohaning said:**
> I think that the rule you added is denying the inbound traffic.

Try this:     ufw deny out to any port 80

It denies all outbound traffic from this machine to any remote port 80.

It works like a charm thank you..How to delete the above rule...

---

