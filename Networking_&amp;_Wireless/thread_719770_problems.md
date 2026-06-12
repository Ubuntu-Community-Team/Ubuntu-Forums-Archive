---
title: "problems"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by laura eznarriaga on 2008-03-09
Hi All,

I have just made a fresh install of ubuntu 7.10 on my computer.
Wifi connection is working great through the Network Manager panel applet but I must start it manually each time I open a session.

I've checked System -> Preferences -> Session -> Startup Programs and "Network manager" is enabled.

Any idea about why it doesn't connect automatically ?

---

### Post by Hightide on 2008-03-09
Hi Laura

what kind of wireless setup do you have?  card or usb?

can you post output of

```
sudo lshw -C network 
```

regards

:)

---

### Post by Eiríkr on 2008-03-09
Network Manager is known to be somewhat weak in terms of features, and it presently does *not* save any login information between boots.  Have a look at [thread=711451]this thread[/thread] for a possible Network Manager replacement.  

Cheers,

Eiríkr

---

