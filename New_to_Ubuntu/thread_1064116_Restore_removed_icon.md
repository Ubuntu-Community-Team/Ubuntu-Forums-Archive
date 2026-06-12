---
title: "Restore removed icon"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by bob brazie on 2009-02-08
I seem to have removed the little red icon from the top far right panel that had my computer name beside it.

It would let me log off and do other tasks.

How can I get this back?

Thanks in advance. Bob.

---

### Post by drs305 on 2009-02-08
Right click the panel, Add to Panel

For just the red symbol:, add "Logout".

If you are talking about the red symbol plus your name, it's called "User Switcher".

---

### Post by bob brazie on 2009-02-08
Thanks, that did the trick. I wasn't looking for that icon on the add page.

Thanks again. Bob.

---

### Post by randysilverwolf on 2009-03-17
Where else can user switcher be found? I have the same problem, and its not in my "add to panel" list

---

### Post by drs305 on 2009-03-17
> **randysilverwolf said:**
> Where else can user switcher be found? I have the same problem, and its not in my "add to panel" list

You can try to install/reinstall it via synaptic or cli - the name is fast-user-switch-applet. It should then show up as "User Switcher" in the *Add to Panel* options.
```

sudo apt-get install fast-user-switch-applet

```

---

