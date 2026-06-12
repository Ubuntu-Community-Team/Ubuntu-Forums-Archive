---
title: "Can't upgrade to 10.10"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by gerardo.siete on 2010-10-10
So, I just tried to upgrade my system to 10.10. My 10.04 system is already up to date. I keep pressing the "check" button on the upgrade manager and nothing comes up. Do I need to do anything special before upgrading? Or am I just too early. I live in the US. and it is 1044am.

Any help is very appreciated. 

Thanks. :)

---

### Post by superninja on 2010-10-10
Open a terminal and type "update-manager -d" without the quotes. An Update Manager window should appear and click upgrade :).

---

### Post by migs73 on 2010-10-10
Open the update manager and click on settings.
In this click on the 'Updates' tab. Check the bit at the bottom thats says Release updates, is set for 'Normal releases', otherwise update manager will ignore the new release.

---

### Post by gerardo.siete on 2010-10-10
Yay! That worked... see ya guys in a bit :)

Thank you by the way!

---

### Post by kaldor on 2010-10-10
Apart from servers, I usually don't recommend upgrading. It's better to do a fresh install after waiting a while.

---

### Post by amjjawad on 2010-10-10
> **kaldor said:**
> Apart from servers, I usually don't recommend upgrading. It's better to do a fresh install after waiting a while.

Why? just for my info :)

---

### Post by migs73 on 2010-10-10
Yeah, I now do fresh installs too. My boot times for a Karmic to Lucid upgrade was over 45s. After wiping and re-installing fresh (now with a separate /home partition) it dropped to 27s. I am now dual booting Lucid and Maverick sharing my home, till I get everything I need set up. Then I can wipe Lucid.

---

