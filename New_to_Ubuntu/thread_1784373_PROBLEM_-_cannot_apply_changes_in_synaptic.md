---
title: "PROBLEM - cannot apply changes in synaptic"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by doublewitt on 2011-06-16
Using Ubuntu 10.04 LTS

Synaptic no longer on the Administration tab - cannot launch from there anymore - but I can launch it with Launchy. The problem after that when launching synaptic, is that when starting, it warns me that: 

"Starting without administrative priveleges

You will not be able to apply any changes. But you can still export the marked changes or create a download script for them."

What happened?
What did I do to cause this?
What can I do to fix this?

Any help would be appreciated...

---

### Post by snowpine on 2011-06-16
Try "gksu synaptic" instead of "synaptic".

"gksu" is short for "graphical sudo" and will execute Synaptic with administrative rights.

---

### Post by doublewitt on 2011-06-16
THANKS - that worked fine! :)

---

