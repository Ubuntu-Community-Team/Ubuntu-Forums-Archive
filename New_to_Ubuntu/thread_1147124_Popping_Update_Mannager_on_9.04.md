---
title: "Popping Update Mannager on 9.04"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by jflarm on 2009-05-03
I only have one complain about 9.04...the annoying behavior of the update manager popping up every once a while.
How do I stop it from popping up??

---

### Post by Zoowey on 2009-05-03
Yeah, this is apparently a new "feature" to make it easier to notice the update manager, apparently some people just couldn't see the notification in the taskbar.

Anyways, simply run this command in the terminal.

gconftool -s --type bool /apps/update-notifier/auto_launch false

You may need to logout for it to take affect.

---

### Post by rburkartjo on 2009-05-03
jflarm or to remove it see this link
[http://www.killertechtips.com/2009/04/26/disable-notifications-in-ubuntu-904-jaunty-jackalope/](http://www.killertechtips.com/2009/04/26/disable-notifications-in-ubuntu-904-jaunty-jackalope/)

---

### Post by Zoowey on 2009-05-03
> **rburkartjo said:**
> jflarm or to remove it see this link
[http://www.killertechtips.com/2009/04/26/disable-notifications-in-ubuntu-904-jaunty-jackalope/](http://www.killertechtips.com/2009/04/26/disable-notifications-in-ubuntu-904-jaunty-jackalope/)

I think he meant the update manager itself and not the notifications.

---

### Post by jflarm on 2009-05-03
> **Zoowey said:**
> I think he meant the update manager itself and not the notifications.

You are right...Thanks Zooney, everything works as it should now!!!

Your command made my day

---

