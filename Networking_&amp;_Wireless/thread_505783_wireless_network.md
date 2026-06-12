---
title: "wireless network"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by wsx123 on 2007-07-20
Is there any kind of program that I can run using Ubuntu 7.04 that will let me know if someone is trying to access my wireless network? I have Ubuntu on my laptop and a wireless router on a windows xp desktop.
Also what is a good firewall for ubuntu 7.04?

---

### Post by wasert on 2007-07-21
I don't know about the program you are looking for, but  try to take a look at the programs included in [http://s-t-d.org/](http://s-t-d.org/) (that's a live distro. with a lot of security related applications)

About the firewall, I've seen people who say the best way to go is to learn iptables and do it all via the command line, but I use firestarter as my firewall application and it works really good I think you can just install it typing:

```

sudo apt-get install firestarter

```

---

### Post by lisati on 2007-09-08
The router I use has an option in its administration page to show attached devices (both wi-fi and cable)  but I don't know about options to log connection attempts.

---

