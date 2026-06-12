---
title: "updates have broken my printer setup"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by gandaran on 2009-04-29
after installing todays jaunty updates my HP printer doesn't work anymore,
in system » administration » printers my printer is gone and I cant add any again as the options are grayed out, anyone know whats going on?

---

### Post by cmnorton on 2009-04-29
There may be renamed files under /etc/cups. You could (as sudo) copy the defns you wanted from the renamed files and put them back into their live counterparts.

---

### Post by gandaran on 2009-04-29
I marked all cups packages in synaptic for reinstall and it's working now got my printer back!

---

