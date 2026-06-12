---
title: "increasing priority on an upgrade"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by jmeXer0 on 2011-05-01
Is there a way to increase the priority on an upgrade once it has already begun?Im familiar with nice and renice but can those be applied to an upgrade?

---

### Post by mr_luksom on 2011-05-07
Yes, they can. 

Get the process ID with

```

ps -e | grep apt

```

Let's say the pid from the command above is 444, and you wanted a priority of- 10.

```

sudo renice -10 444

```

---

