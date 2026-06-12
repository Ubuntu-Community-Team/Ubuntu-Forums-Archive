---
title: "[SOLVED] what is my computer's internal IP address?"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by ryharv on 2007-06-12
Hello everyone,

I'm trying to obtain my computer's LAN IP address (like 192.168.0.1) so I can connect via SSH inside my house, from another computer.

When I run ifconfig, however, all I get on the "inet" line is:

inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host

Any clues?  Probably an easy solution but I can't figure it out.  Thank you!

---

### Post by ryharv on 2007-06-12
oh my god, I am retarded.  I didn't have the box plugged into an ethernet cable.

---

### Post by ryharv on 2007-06-12
well, that didn't solve the problem.  any help?  thank you!

---

### Post by croto on 2007-06-12
does internet work after you plug in the cable?

---

### Post by ryharv on 2007-06-12
yeah, i can connect to the internet but running ifconfig does not tell me the computer's IP address.

---

### Post by croto on 2007-06-12
Then I guess that ifconfig should give you the IP. Can you post the output of **ifconfig -a** ?

---

### Post by tturrisi on 2007-06-12
```
ifconfig  | grep 'inet addr:'| grep -v '127.0.0.1' | cut -d: -f2 | awk '{ print $1}'
```

---

### Post by H3g3m0n on 2007-06-12
Right clicking on the network manager icon (top right) and selecting connection information will also work if you want a simple gui way.

---

### Post by ryharv on 2007-06-12
actually, i got it working.  i ran **ifdown eth0** and then **ifup eth0**, to restart the networking, and then an inet address showed up in ifconfig.  thanks all for your help!

---

