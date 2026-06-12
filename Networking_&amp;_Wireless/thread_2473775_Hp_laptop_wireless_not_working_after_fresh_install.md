---
title: "Hp laptop wireless not working after fresh install"
date: 2022-04-13
forum: Networking &amp; Wireless
---

### Post by jmichaels29 on 2022-04-13
Ubuntu 20.04 LTS

HP laptop wireless not working after fresh install.

Please help

Absolutely no attempt of it to detect any wireless signal(s),  Ubuntu also has no place on upper right to even try to access wireless.

If someone could tell me some command lines to try to check on and attempt to get wireless hardware inside computer to start up I would appreciate it.

See attachment as to all I get:

---

### Post by jmichaels29 on 2022-04-13
Solved problem by installing "Additional Drivers" from software center and running in terminal: "sudo apt-get install --reinstall bcmwl-kernel-source" and reboot.

---

