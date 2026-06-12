---
title: "remote desktop to Hardy not working"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by twinspop on 2008-08-29
Vino-server only listens on ipv6. I've tried forwarding ipv6 through an ssh tunnel, but I'm getting nowhere. I've already left work, and only have ssh access to the box. Any ways except vino-server to get to the desktop?

netstat -na | grep 5900
tcp6       0      0 ::1:5900                :::*            LISTEN     


Thanks,
jon

---

### Post by Mister.Vash on 2008-08-29
They still haven't fixed the issue:
[https://bugs.launchpad.net/ubuntu/+source/vino/+bug/228370](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/228370)

The third post in this thread works for me
[http://ubuntuforums.org/showthread.php?t=518965](http://ubuntuforums.org/showthread.php?t=518965)

---

### Post by twinspop on 2008-08-30
Thanks. I had tried that with no luck. However, thinking I must have done something very simple wrong, I used an X session for vino-preferences and reset the password. Voila!

Jon

---

