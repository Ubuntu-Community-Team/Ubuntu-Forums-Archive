---
title: "I am having a problem with activating my wireless?"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by Billy000 on 2009-12-27
I'm sure this question is a dime-a-dozen, so for that I apologize. I looked at other threads having the same problem but the solutions proposed in those threads didn't help.

I don't seem to have a system notification area nor do I have the NetworkManager icon like it says in the printed instructions. Any suggestions?

---

### Post by LuisGMarine on 2009-12-30
Hopefully you can hook up that PC to a network using an ethernet cable.  If you can do that, from the machine open up Terminal ( Applications > Accessories > Terminal)

and type in the following, and paste the outputs:
```

sudo lshw -C network
```

if network manager is still not installed, run:

```
sudo apt-get update && sudo apt-get install wicd
```

---

