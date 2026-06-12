---
title: "wired connection assigned new device id on every boot..."
date: 2008-03-14
forum: Networking &amp; Wireless
---

### Post by nutz on 2008-03-14
I have this weird issue where my NIC gets assigned a new device ID every time my laptop boots. Right now it is eth40 and if I reboot it will be eth41...

Has anyone experienced this issue before?

---

### Post by handydan918 on 2008-03-14
> **nutz said:**
> I have this weird issue where my NIC gets assigned a new device ID every time my laptop boots. Right now it is eth40 and if I reboot it will be eth41...

Has anyone experienced this issue before?
There was a report of a similar incident [here]("http://mepislovers.org/forums/showthread.php?t=14469")

If after looking that link over, you haven't resolved it, post back with the output of ```
lspci | grep -i net
```

---

### Post by nutz on 2008-03-14
That link doesn't want to work for me. Could you double check it?

---

### Post by handydan918 on 2008-03-14
> **nutz said:**
> That link doesn't want to work for me. Could you double check it?

That's interesting...it works for me...

But here's the URL...

[http://mepislovers.org/forums/showthread.php?t=14469](http://mepislovers.org/forums/showthread.php?t=14469)

---

