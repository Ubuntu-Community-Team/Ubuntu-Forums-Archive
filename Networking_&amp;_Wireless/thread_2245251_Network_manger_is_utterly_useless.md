---
title: "Network manger is utterly useless"
date: 2014-09-22
forum: Networking &amp; Wireless
---

### Post by himself2 on 2014-09-22
I've had three laptops running different versions of Ubuntu and one thing that has always got on my nerves is network manager stopping to connect to any network, wireless or wired. How is that my age old phone can connect to a network in an instant but my new laptop with the latest version of Ubuntu can't and not just that, it doesn't give any freaking message as what the problem is. How is that windows NM gives you error messages but Linux's one (which is used by control freaks) doesn't? 

When this happens I do all kinds of things, check wifi power management, restart network manager, nm-applet or the computer itself, banging my head to the wall but no help. I can only pray god for some miracle.

Dear Ubuntu developer, please don't care about correcting simple bugs in the most important apps, just rush to prepare the next release with a funny name.

I don't mean to be ingrate toward free software developers but I never understood the impulse for having to new releases each year without caring enough bout fundamental issues.

---

### Post by slickymaster on 2014-09-22
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by tgalati4 on 2014-09-22
NetworkManager is a complicated framework.  When it works, it works well.  When it doesn't, you start pulling your hair out.

Open a terminal and post the output of:

```
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
```

for just one problematic computer.

Read up on [NetworkManager]("https://help.ubuntu.com/community/NetworkManager") so you can appreciate what it can do.

If you install ANY other network manager or make ANY changes to the configuration files above, you will find yourself here.

---

