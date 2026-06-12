---
title: "Upgrade to 10.04 from 8.04?"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by sillyboy on 2010-07-22
Is it possible to upgrade to 10.04 from 8.04 without losing my files, settings, etc?

Thanks

PS Did a search and nothing showed up...

---

### Post by snowpine on 2010-07-22
Yes, it is possible:

[http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

---

### Post by new__buntu on 2010-07-22
Update manager can upgrade you to 10.04, but there will be multiple, long downloads involved.

---

### Post by philinux on 2010-07-22
> **sillyboy said:**
> Is it possible to upgrade to 10.04 from 8.04 without losing my files, settings, etc?

Thanks

PS Did a search and nothing showed up...

Is /home on it's own partition? Personally I would backup important stuff and do a clean instal with a separate home partition.

---

### Post by bodhi.zazen on 2010-07-22
> **new__buntu said:**
> Update manager can upgrade you to 10.04, but there will be multiple, long downloads involved.

Define "multiple, long downloads".

The upgrade LTS -> LTS is direct, so, yes essentially every package will need to be upgraded. Some may need to be removed and some installed, but you do **not** need to go 

8.04 -> 8.10 -> 9.0-4 -> 9.10 -. 10.4

---

### Post by new__buntu on 2010-07-22
> **bodhi.zazen said:**
> Define "multiple, long downloads".

The upgrade LTS -> LTS is direct, so, yes essentially every package will need to be upgraded. Some may need to be removed and some installed, but you do **not** need to go 

8.04 -> 8.10 -> 9.0-4 -> 9.10 -. 10.4

8.04 -> 8.10 -> 9.0-4 -> 9.10 -> 10.4 was my experience when I tried to use update manager. Well, technically 8.04 -> 8.10 -> 9.0-4 -> 9.10 ->fried comp->10.04 was my experience (apparently the update manager didn't like me using a KVM switch while it was working). Was there something that I did wrong to make it so I had to go 8.04 -> 8.10 -> 9.0-4 -> 9.10 -> 10.4?

---

### Post by bodhi.zazen on 2010-07-22
> **new__buntu said:**
> 8.04 -> 8.10 -> 9.0-4 -> 9.10 -> 10.4 was my experience when I tried to use update manager. Well, technically 8.04 -> 8.10 -> 9.0-4 -> 9.10 ->fried comp->10.04 was my experience (apparently the update manager didn't like me using a KVM switch while it was working). Was there something that I did wrong to make it so I had to go 8.04 -> 8.10 -> 9.0-4 -> 9.10 -> 10.4?

Well Upgrades can always go wrong, and often for reasons that are not your fault. Before I upgrade I back up my data and if the upgrade goes bad I follow your prescription, fresh install.

Generally, upgrades go well enough if you wait at least a few days, 2-4 weeks after the release. Give a little time to work the bugs out.

In terms of missing something, see the upgrade page:

[http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

The third section is "Upgrade from 8.04 LTS to  10.04 LTS"

HTH.

---

