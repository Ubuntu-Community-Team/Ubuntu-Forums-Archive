---
title: "How to refresh hosts file without rebooting"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by karthick87 on 2010-06-09
Every time when i make changes to hosts file it requires a restart to work properly,is there any alternate way to refresh the hosts file without restarting the system..?

---

### Post by cariboo on 2010-06-09
What kind of changes are you making to the hosts files? All you should be using the host file for is aliasing a computer name to it's ip address. If you are setting up aliases to virtual web sites, you should only have to restart apache2:

```
sudo apache2 restart
```

---

### Post by bodhi.zazen on 2010-06-09
> **getyourkarthick said:**
> Every time when i make changes to hosts file it requires a restart to work properly,is there any alternate way to refresh the hosts file without restarting the system..?

I have not seen that behavior. After editing the hosts file it takes effect immediately.

What (application or server) are you having a problem with ?

---

### Post by doas777 on 2010-06-09
assuming that hosts does need refreshed (i haven't the foggiest), I would guess that restarting the networking service would do it.

```

sudo /etc/init.d/networking restart

```

---

### Post by ka55o5 on 2013-04-09
> **doas777 said:**
> ```
sudo /etc/init.d/networking restart
```

.. is now (Quantal):

```
sudo service networking restart
```

However, this does not seem to reload my ***hosts***? :-0

**Edit**: Ah, for crying out loud, Firefox needed restarting after the change. :\

---

### Post by oldos2er on 2013-04-10
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

