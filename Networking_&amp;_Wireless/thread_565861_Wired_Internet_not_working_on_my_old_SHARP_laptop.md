---
title: "Wired Internet not working on my old SHARP laptop"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by DilfATX on 2007-10-02
I have GG 7.10 installed on my old SHARP notebook.. it picks up wireless cards for internet very easily..but not wired.. when I go to plug in my ethernet (cable internet) into it I see that it does recognize it and says connected but I can't get to the internet.. any help guys?

---

### Post by noob12 on 2007-10-02
Can you gather this information and post it

Grab these any time
```

lspci -nn

sudo lshw -C network

```

Grab these when you are hooked up wired.
```

sudo ethtool eth0

ifconfig -a

route -n

```

---

