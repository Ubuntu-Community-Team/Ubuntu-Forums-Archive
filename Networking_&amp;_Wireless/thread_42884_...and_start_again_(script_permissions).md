---
title: "...and start again (script permissions)"
date: 2005-06-19
forum: Networking &amp; Wireless
---

### Post by Dave_is_sexy on 2005-06-19
Oh. Great it's all broken... I think that was my fault. Anyhow I'm setting up the net again. Hapily I know that procedure by heart now. Unfortunately I can't remember how to get the dial script to run at start up and be allowed to run from any account. I did get this sorted before and saved the script, but I have to put it somewhere and give it certain permissions somehow. Anyone know? Thanks

---

### Post by diebels on 2005-06-20
Put it in /etc/init.d/ and make a link to /etc/rc2.d
chmod 6755 to allow everybody to run it.

---

