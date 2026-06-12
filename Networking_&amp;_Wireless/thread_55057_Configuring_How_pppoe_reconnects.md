---
title: "Configuring How pppoe reconnects"
date: 2005-08-07
forum: Networking &amp; Wireless
---

### Post by anwarlorenzo on 2005-08-07
Let's say my dsl connection suddenly drops. What file do I need to edit on how many times pppoe reconnects and in how many time intervals(in secs)? Acually I want it to reconnect immediately on unlimited number of times.

---

### Post by Spleenie on 2006-08-06
> **anwarlorenzo said:**
> Let's say my dsl connection suddenly drops. What file do I need to edit on how many times pppoe reconnects and in how many time intervals(in secs)? Acually I want it to reconnect immediately on unlimited number of times.

I think I just found this one out myself.

Use your favourite editor to open (as sudo) /etc/ppp/peers/dsl-provider

eg 
```
sudo pico /etc/ppp/peers/dsl-provider
```

Somewhere in there add:

```
maxfail 0
```

I believe this will prompt your dialer to continually attempt reconnection.

Let me know if it works out.

---

