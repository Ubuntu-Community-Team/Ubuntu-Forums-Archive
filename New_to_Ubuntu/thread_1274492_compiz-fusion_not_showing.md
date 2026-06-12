---
title: "compiz-fusion not showing?"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-09-24
i downloaded it it says it on my synaptic that i have it... but its not a option in my preferences bar so now what do i do?
thanks!

---

### Post by rajeev1204 on 2009-09-24
> **R3fr4cti0n said:**
> i downloaded it it says it on my synaptic that i have it... but its not a option in my preferences bar so now what do i do?
thanks!

Its already installed by default on ubuntu.

Go to menu>system>appearances>visual effects and turn it on.

It will only work if your graphics card supports 3d rendering.

That can be checked in a terminal by typing...

```
glxinfo | grep render
```

---

### Post by Marflus on 2009-09-24
The package you need to install in order to configure Compiz from your preferences menu is *compizconfig-settings-manager*. 

```

sudo aptitude install compizconfig-settings-manager

```

---

