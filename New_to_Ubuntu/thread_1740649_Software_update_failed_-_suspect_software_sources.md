---
title: "Software update failed - suspect software sources"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by geezerone on 2011-04-27
Last couple of days when performing software update am getting some 404 errors. Checked the sofware sources and pinned it down to the following:

[http://ppa.launchpad.net/ppa/ppa/ubuntu](http://ppa.launchpad.net/ppa/ppa/ubuntu)   --- Maverick Main
[http://ppa.launchpad.net/ppa/ppa/ubuntu](http://ppa.launchpad.net/ppa/ppa/ubuntu)  --- Maverick source code

These aren't valid urls but don't know why they have gone?

Anyone else with similar issues and what these could be pointing to?

---

### Post by Frogs Hair on 2011-04-27
Go to launchpad and check to see if the PPA is still valid .  PPA projects are somtimes dropped by the developer for different reasons .

---

### Post by Frogs Hair on 2011-04-27
I wanted to add that if the PPA is no longer supported you can continue to use the software , just remove the source from the sources list and you won't bothered with errors at update .

---

