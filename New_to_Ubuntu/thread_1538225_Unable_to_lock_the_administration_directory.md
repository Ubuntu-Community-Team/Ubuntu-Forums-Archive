---
title: "Unable to lock the administration directory"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by TimEnid on 2010-07-24
what does this mean, and how can i fix this. I am trying to install Wine, and this is what i get

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Darkness Des on 2010-07-24
It means that you have a Synaptic or Update Manager window open while try to install Wine. Even that "Window that doesn't show up on the panel" window will make it do that.

---

### Post by TimEnid on 2010-07-24
ahhhh, i see. thanks. i did have synpatic opened.

---

