---
title: "Is there any way to load a driver for a wired network card?"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by SirScott13 on 2009-03-24
I have an old laptop that doesn't have an integrated network card.  I am trying to get xubuntu to recognize the network card.  When I run lspci, it sees the hardware, but I don't think that there is a driver associated with it.  The computer is a Dell CPt and the card is a Microsoft MN120.  Any help would be appreciated.

---

### Post by cariboo on 2009-03-24
Your network adapter is supposed to use the tulip driver. Do you see any mention of the driver if you run in a terminal:

```
lsmod | grep tulip
```

Could you also paste the output of:

```
sudo lswh -C network
```

in your next post.

Jim

---

### Post by plucky on 2009-03-24
> sudo lswh -C network

That would be ```
sudo lshw -C network
```

---

