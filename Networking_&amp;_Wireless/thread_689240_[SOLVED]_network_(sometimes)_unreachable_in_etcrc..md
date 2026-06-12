---
title: "[SOLVED] network (sometimes) unreachable in /etc/rc.local?"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by jjalocha on 2008-02-06
I am trying to set-up a permanent SSH-tunnel, thus I am putting the ssh -R in /etc/rc.local. the strange thing is that sometimes (very few) the connection is built as expected, but most times I get no connection at all:

```

ssh: something.net: Name or service not known

```

The address is correct, since it does sometimes work, and the server is working, since I **always** can connect and ping manually. The problem only happens when running from rc.local.

First I thought it might be an IP problem, so I added the host to /etc/hosts, but the same problem. A very few times it connects on startup, but most times I just get an error:

```

ssh: connect to host something.net port 22: Network is unreachable

```

Since I never have any problems connecting manually, I think it might be that the network is just slow to start up, so I added a line with 'sleep 2' before the 'ssh -R etc', but to no avail.

Any ideas what might be wrong, or how to work around this? I really need a reliable tunnel!

(I was also trying to use autossh for a more reliable connection. But it didn't work, probably because of this very same issue, so I will try to fix this with ssh first.)

---

### Post by jjalocha on 2008-02-06
I solved this issue.
I just have to use a very long pause for the network connection to come up. I am using 'sleep 20' and it works fine now.

---

