---
title: "Surpress username w RDesktop XP Login"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by RMOP on 2008-11-25
It's a small thing, but I don't want rdesktop to supply a username to my XP login prompt. I found no way to suppress the username from being filled if I used Terminal Server Client. However, if I run rdesktop from a script, I get what I want:

rdesktop -g 92% -u '' 192.168.xx.xxx

The -g allows me to set a screen size which works for my eee PC, and the -u option followed by the (empty) pair of single quotes '' forces the XP login prompt to be empty.

---

