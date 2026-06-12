---
title: "Can't update"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by Bo0ddha on 2010-12-11
just installed ubuntu 10.10 and went to do the updates.  Everytime I click update it just comes back and says packaged isnt installed  No need for a removal.  Then I click close and it stops.

---

### Post by sikander3786 on 2010-12-11
Go to Applications > Accessories > Terminal and post the output of this command.

```
sudo apt-get update && sudo apt-get upgrade
```

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

### Post by Bo0ddha on 2010-12-11
```
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

So I know a reboot would fix this, but is there a better way to do it?  I've hit this earlier today.

---

### Post by sikander3786 on 2010-12-11
Make sure no other package manager like Synaptic, Software Center, Update Manager, aptitude or even another instance of apt-get is not running. If running, close that and try the above command again.

For the time being, if no other package manager is running, I would suggest a simple reboot.

---

