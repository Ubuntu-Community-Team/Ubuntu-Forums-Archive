---
title: "connecting to the net"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by jaybird9981 on 2007-08-13
It says I am connected to the net but I can't do anything in Firefox or chat on messenger. I am connected with a wire to my motherboard. I am using comcast and have a cable modem. what is weird I can connect just fine at my friends house but not at mine.I wonder why I can't do anything but it says I am connected. :confused:

---

### Post by noob12 on 2007-08-13
Posting the output of these commands will help people diagnose it
```

ifconfig -a

/sbin/route -n

cat /etc/resolv.conf

```

---

### Post by jaybird9981 on 2007-08-13
it says -n is an unknown host what does what mean?

---

### Post by noob12 on 2007-08-13
> **jaybird9981 said:**
> it says -n is an unknown host what does what mean?

OK.  You might be getting some other route command. I fully qualified the command name in my previous post.  Please try again.

By the way, where are you typing those commands?  What's intended is that you should open a terminal window using Applications | Accessories | Terminal.  Type the commands in that window.

---

