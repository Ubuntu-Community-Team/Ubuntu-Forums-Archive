---
title: "Can't seem to upgrade - help!"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by furoido on 2008-12-03
For the past couple of weeks my upgrade manager has been telling me that I have 7 upgrades available. Yet when I try to install them, I keep on being told they cannot be installed. Same thing even if I try a partial upgrade...any suggestions on how to resolve?

I'm using Hardy Heron, by the way.

---

### Post by Dj Melik on 2008-12-03
Open terminal run these commands:

```
sudo apt-get update
sudo apt-get upgrade
```

If you get a error, copy paste it back here.

---

### Post by furoido on 2008-12-03
You're an angel, Dj! Many thanks!

BUT I just re-opened update manager to double-check and although it says my system is now up to date, I still get the "Not all updates can be installed" warning box?!

---

### Post by Dj Melik on 2008-12-03
Go to System > Administration > Synaptic

and in Synaptic click on Mark All Upgrades, that should remove the package that is causing problems. 

Have you tried upgrading your entire system to Ubuntu 8.10?

You can do this by:

1) Pressing Alt + F2
2) Typing in **update-manager -d**
3) Press Run.

---

### Post by furoido on 2008-12-03
Seems to have done the trick, thank Dj!

---

### Post by furoido on 2008-12-03
Ah, that is something I have been wondering about! Is upgrading to Ibex worthwhile?

---

### Post by Dj Melik on 2008-12-03
Yeah, I would say so. The system is a lot more organized and efficient.

And no problem, glad to help =)

---

### Post by furoido on 2008-12-03
Dj, did as you suggested, but my update manager tells me everything is up to date! Does that means I have already updated to Ibex without realising it?? Can't say I notice anything different, though...

---

### Post by perlluver on 2008-12-03
Go to System>Administration>System Monitor, and click on the first tab System.  And see what it says.

---

