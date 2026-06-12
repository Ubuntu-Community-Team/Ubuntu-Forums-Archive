---
title: "Bloody proxy settings in terminal"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by humphreybc on 2009-09-30
Hi guys,

I have my proxy setup for Synaptic and also System wide proxy, but terminal still doesn't work with the proxy.

I've added lines to /etc/bash.bashrc and /etc/environment and /etc/apt/apt.conf but nothing seems to work.

I've looked all over the internet and there seem to be a dozen ways of doing it, but which one is the *right* way!?

---

### Post by ken22 on 2009-09-30
add ```
export http_proxy="*proxy.example.com:port*"
```

to .bashrc

altering it to your actual proxy details.

---

### Post by humphreybc on 2009-09-30
Thanks, that fixed it. So I can remove all the extra crap in those other files?

---

### Post by ken22 on 2009-09-30
yes, but this setting won't apply to synaptic. This will apply to the terminal for you and no other user.

that cool?

---

### Post by humphreybc on 2009-09-30
> **ken22 said:**
> yes, but this setting won't apply to synaptic. This will apply to the terminal for you and no other user.

that cool?

Righto, gotcha.

Why does "Apply System Wide" not apply the settings to terminal?

---

### Post by ken22 on 2009-09-30
I would assume that the terminal is a separate instance of login, but don't quote me on that.

---

