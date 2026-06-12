---
title: "IP address change"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2011-04-27
I'm running wubi 10.04. How do I change my IP address?

Thanks in advace.:)

---

### Post by bioterror on 2011-04-27
> **Inodoro Pereyra said:**
> I'm running wubi 10.04. How do I change my IP address?

Thanks in advace.:)


Open terminal and type:

```
man ifconfig
```

sudo ifconfig eth0...

---

### Post by coffeecat on 2011-04-27
> **Inodoro Pereyra said:**
> I'm running wubi 10.04. How do I change my IP address?

Which IP address, your LAN address or your WAN address? Do you use a router on your local network?

For your LAN address, some routers enable to you set up a static IP address for designated devices. Alternatively, you can use the network manager applet within Ubuntu. Right-click on the NM applet in the upper panel (I presume you're using Ubuntu/gnome - wubi makes no difference here), and choose "Edit connections". Go to the wired or wireless tab as appropriate, and now highlight the connection > Edit > IPv4 Settings tab and set up a static IP address.

If you mean the WAN IP address, you'll have to talk to your ISP.

---

### Post by Inodoro Pereyra on 2011-04-27
Thanks guys. It wasn't an IP address problem after all. Already figured it out.:)

---

