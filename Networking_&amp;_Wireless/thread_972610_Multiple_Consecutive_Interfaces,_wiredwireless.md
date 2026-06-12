---
title: "Multiple Consecutive Interfaces, wired/wireless"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by jamescondron on 2008-11-05
Sorry if this has been asked and answered, either my google'ing/ forum searching is crap, or it hasn't. (Yes, I know that seems to top most posts, but I really did search ;) )

Background, I suppose: I have a box I use for coding, experimenting etc., and a box I use for day to day. I'm currently in halls at a university and can only use one connection, registered to a MAC address.

I want to sorta network my two together and set up an NFS thing. This is easy and I have done it. My main question, though, is whether Ubuntu can use two Network Interfaces at once. I have the two boxes hooked up to a wireless router, but cannot use this to share my connection, partially because it is easy to track, partially because when I set up the connection, only one box was with me.

Ideally, I would like to keep my day-to-day machine wired into the halls network, and then use it to wirelessly(sp?) connect to the router which my coding box is always connected to, though at the same time. Is this possible? Will ubuntu allow me to set up the network file system over wireless (ipw2200) and use the wired connection for everything else?

Or will I have to disconnect one to use the other? Am I doomed to using bad dbus driven scripts to facilitate this? Will the Earth be saved before bedtime by the powerpuff girls? Should I go just shut up and use a system I can't hurt myself on?

Really, I Just Don't Know (tm)

---

### Post by jpkotta on 2008-11-06
[http://ubuntuforums.org/showthread.php?t=503287](http://ubuntuforums.org/showthread.php?t=503287)

Why can you only have one machine connected?  Sounds like a weird policy.

---

### Post by cariboo on 2008-11-06
Most routers allow you to clone a mac address. You could clone the registered mac address and share the connection between the two computers.

Jim

---

### Post by jpkotta on 2008-11-06
You will also have to change the MAC address of your computer, if you change the MAC of the router.
```
sudo ifconfig eth0 hw ether XX:XX:XX:XX:XX:XX
```

---

