---
title: "static ip dns lookup"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by monkeyking on 2007-07-05
Hi, this problem has probly been asked a kazillion times. But I can't find the solution.


I'm on a network with some computers that need static ip adr.
So I just changed the
```

/etc/network/interfaces

```

That works like a breeze.

So now I can ssh to the static ip computers.
That is I need to type in the ipadr when I ssh.

And that's stupid.


Before when these computers had a dynamic ip, all computers on the network could ping these computers just knowing their hostname.

I somehow need to add the computer with the static ip adr. to the network dns or something.

Anybody knows?

thanks in advance

---

### Post by Mr. C. on 2007-07-05
You haven't described your DHCP / DNS setup, so no answers can be provided yet.  Please elaborate and explain.

If you are using a DNS server, then you need to update your DNS server with hostname to IP address records (A records).   If your router provided this for you, you'll have to either setup your own DNS server, or configure the /etc/hosts files on various systems.  There are other mechanisms too, but let's just start with this until you explain more about your setuip.

MrC

---

