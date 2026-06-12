---
title: "installing deb package problem"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by mike22 on 2009-01-02
Hi, I'm trying to install a deb package on my computer. I get a message saying that only one software management tool is allowed to run. I don't have any software management tools running. Thanks.

---

### Post by Kosimo on 2009-01-02
> **mike22 said:**
> Hi, I'm trying to install a deb package on my computer. I get a message saying that only one software management tool is allowed to run. I don't have any software management tools running. Thanks.

DO you have some terminal open? 
If the problem persists, just try the easiest way which is restarting your computer.

---

### Post by 2hot6ft2 on 2009-01-02
Close synaptic, terminals, add/remove apps, and if the updater icon is showing on the top task bar wait for it to go away.

Only 1 installer can run at a time since the installer has to have a lock on the installation process.

---

### Post by albinootje on 2009-01-02
> **mike22 said:**
> Hi, I'm trying to install a deb package on my computer. I get a message saying that only one software management tool is allowed to run. I don't have any software management tools running. Thanks.
After you boot your machine the update-manager will check for new updates when you're online.
It's possible that that was the case.

---

### Post by mike22 on 2009-01-03
Is there any p2p programs I can install from synaptic, or would I get the same message?

---

### Post by albinootje on 2009-01-03
> **mike22 said:**
> Is there any p2p programs I can install from synaptic, or would I get the same message?

Try it.

If you get the same error, please post the output of :
```

lsof|grep apt

```

---

