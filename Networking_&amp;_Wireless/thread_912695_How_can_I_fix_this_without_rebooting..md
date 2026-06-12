---
title: "How can I fix this without rebooting."
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by esac on 2008-09-07
I was just online 5 minutes ago when the network went completely down. My wifes computer was working, so I looked at mine, and the wireless had completely shutdown. "Enable Wireless" was greyed out. My wireless switch was on, tried the Fn+F5 key to enable it, and then "sudo /etc/init.d/networking restart" with no luck.

When things like this happen are there other things I can use to try to recover?

---

### Post by dmizer on 2008-09-07
Only have a terminal option for you.  You can try running the following command:

```
sudo /etc/init.d/networking restart
```

If that doesn't work, I have a few other ideas.

---

### Post by dmizer on 2008-09-07
Only have a terminal option for you.  You can try running the following command:

```
sudo /etc/init.d/networking restart
```

If that doesn't work, I have a few other ideas.

---

### Post by esac on 2008-09-07
> **dmizer said:**
> Only have a terminal option for you.  You can try running the following command:

```
sudo /etc/init.d/networking restart
```

If that doesn't work, I have a few other ideas.

I tried that, it didn't work :(

---

### Post by dmizer on 2008-09-07
I suppose it would have helped if I read more carefully. Sorry.

Well, what IP address do you get when you are online? And, what IP address does your wife get when she goes online and kicks you off?

---

