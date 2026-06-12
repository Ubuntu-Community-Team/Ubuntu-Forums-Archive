---
title: "security probs with update"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by abooks on 2008-12-16
I'm trying to get updates (using terminal) and I got most, but the last ones say "could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?"

I downloaded 160 upgrades yesterday, but this last group seems to be balking. Any ideas?

---

### Post by Tatty on 2008-12-16
Usually that message is given if you have another package manager running at the same time.  Do you have synaptic open?

If there are no other package managers running then did you put sudo at the start of the command?

---

### Post by abooks on 2008-12-17
I didn't have synaptic open, but per instructions, I used sudo apt-get to get update, then got upgrade without.

---

