---
title: "Enabling IP forwarding in Hardy Heron?"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by needhelpplease on 2008-05-03
I know, it's a basic question, but believe me, I've looked all over on Google before asking here.

How do I permanently enable IP forwarding on Hardy?

I can do it for one boot session by:

```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

But I don't want to have to do that every time I boot.

I also put 

```
net.ipv4.conf.default.forwarding=1
```

in ```
/etc/sysctl.conf
``` , but that didn't do the trick either.

What am I missing?  Is there some GUI tool that does advanced net configuration that I should be using, or some other config file I'm not finding?

Thanks

---

### Post by needhelpplease on 2008-05-03
Ah, with some more searching, I found this thread about [IP forwarding in Ubuntu](http://ubuntuforums.org/showthread.php?t=553024) which explains what to do.

---

### Post by AnRkey on 2008-11-23
> **needhelpplease said:**
> I know, it's a basic question, but believe me, I've looked all over on Google before asking here.

How do I permanently enable IP forwarding on Hardy?

I can do it for one boot session by:

```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

But I don't want to have to do that every time I boot.

I also put 

```
net.ipv4.conf.default.forwarding=1
```

in ```
/etc/sysctl.conf
``` , but that didn't do the trick either.

What am I missing?  Is there some GUI tool that does advanced net configuration that I should be using, or some other config file I'm not finding?

Thanks

Thanks for the kick in the right direction. This fixed my poptop issue.

It's net.ipv4.ip_forward=1 and not net.ipv4.conf.default.forwarding=1 in the /etc/sysctl.conf that fixed it for me.

R

---

