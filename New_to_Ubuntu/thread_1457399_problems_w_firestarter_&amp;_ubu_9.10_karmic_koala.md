---
title: "problems w/ firestarter &amp; ubu 9.10 karmic koala"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-04-18
I'm having a problem w/ firestarter.  I get an error message saying: "failed to start firewall the device eth0 not ready" this happens randomly.  Sometimes everything is fine.  when i ran the setup wizard i noticed that there is no eth1 only eht0 and eth2.  I'm including a screenshot to show you guys what I'm talking about.  Let me know what you think!  BTW I'm using my wifi connection right now so I guess that's eth2. oh and yes, the network is working fine.  I'm on the 'net right now.  I'm open to all meaningful thoughts and ideas.

---

### Post by J V on 2010-04-18
It seems to expect a wired connection...

Please see pre-made post for reasons you want to stay away from firestarter...

> **Firewall**
Ubuntu comes with a fantastic firewall known as iptables. It is inactive by default, because no applications are "Listening" to the ports (Doorways) on your computer anyway, so there is no need for a firewall unless you install a server of sorts (And if you are installing servers you should know this already)

Iptables is actually very hard to configure, you need to edit configuration files, know the program, its just much more advanced. Luckily, there are tools that make this easy.

The most often advised firewall interface is "Firestarter", but nowadays its a bad idea to use it. It hasn't been developed for ages now, and because ufw (A command line configuration tool) is installed, Firestarter will conflict with already running services.

On top of that, while it runs, it runs as root, so if someone were to exploit a vulnerability in Firestarter, it would give them complete access to your system.

The current interface suggestion is "[gufw]("apt://gufw")" (Click to install) which, once again, is not a firewall, but a means to configure the default firewall.

---

### Post by bradmayne04 on 2010-04-18
So you think i should remove firestarter completely? Well, I'll give your suggestion a try.  Thanks

---

