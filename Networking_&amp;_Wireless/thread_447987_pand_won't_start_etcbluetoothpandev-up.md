---
title: "pand won't start /etc/bluetooth/pan/dev-up"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by kuni on 2007-05-18
Hello!
  I am having a minor problem when trying to set up a bluetooth connection between my PDA (running linux) and an Ubuntu Feisty laptop. The connection via pand is OK, though I'd wish to have IP settings automatically loaded when bnep0 is created. The man page (and google :)) says that the script /etc/bluetooth/pan/dev-up is invoked whenever a new bnepN is spawned. Unfortunately, when I create a script in that location, it is not started. I tried running pand with --devup /etc/bluetooth/pan/dev-up option, nothing seems to help. Of course, I assigned the script execute permissions. Thanks for any help! Regards, Kuni

---

### Post by dr_agon on 2007-09-19
Hi!
I have exactly the same problem. Did you solve it?

---

### Post by maximk on 2007-11-27
The same problem in gutsy. Have anyone solved this issue?

---

