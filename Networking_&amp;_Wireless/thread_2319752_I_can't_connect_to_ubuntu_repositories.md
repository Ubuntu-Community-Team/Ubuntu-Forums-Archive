---
title: "I can't connect to ubuntu repositories"
date: 2016-04-06
forum: Networking &amp; Wireless
---

### Post by carlosfrancoba on 2016-04-06
Hey guys
I can't connect my xubuntu to repositories to update it

when i put the this command line, it returns in a message and stucks:
# apt-get update
0% [Conectando em us.archive.ubuntu.com (2001:67c:1562::14)] [Conectando em archive.canonical.com (2001:67c:1360:8c01::1b)] 

can anyone help me?
there is a problem with ubuntu repositories?

i use only canonical official and partners on my sources list, there is no PPA on my sources 

(sorry for my poor english, i'm brazilian)

---

### Post by sammiev on 2016-04-06
Hi,

What version of Xubuntu are you using?

and you are connected to the Internet right?

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

---

### Post by Bucky Ball on 2016-04-06
> **sammiev said:**
> 
```
sudo apt-get update
```

```
sudo apt-get upgrade
```

^^^
This.

You're missing a 'sudo' at the beginning of the command.

---

### Post by QLee on 2016-04-07
Did everyone notice that the OP is at the root prompt and thus shouldn't need sudo?

Looks like maybe an ISP  might be trying to get ready for rollout of ipv6 since that is the failing address. Maybe testing or something or possibly even something along the route. 

Aha, I found a launchpad bug about this:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1412943](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1412943)

---

