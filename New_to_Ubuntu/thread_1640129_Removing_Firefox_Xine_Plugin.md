---
title: "Removing Firefox Xine Plugin"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by zer010 on 2010-12-07
I had installed the Xine plugin for Firefox 3.6.12.  Now it comes up as the default media-player for internet content, instead of Totem.  I disabled the plugin thinking that Totem would be the next default, but I don't get anything! So my question is, How do I remove the Xine plugin and transfer the operations to Totem?

---

### Post by gandaran on 2010-12-07
> **zer010 said:**
> I had installed the Xine plugin for Firefox 3.6.12.  Now it comes up as the default media-player for internet content, instead of Totem.  I disabled the plugin thinking that Totem would be the next default, but I don't get anything! So my question is, How do I remove the Xine plugin and transfer the operations to Totem?
open synaptic package manager, scroll down to the xine plugin and mark for complete removal then click the apply button, if the totem plugin is still installed and enabled you don't have to do anything, the plugin will take over again.

---

### Post by zer010 on 2010-12-07
Thanks! I'll give that a try.

---

### Post by karthick87 on 2010-12-07
```
sudo apt-get remove xine-plugin
```

---

### Post by zer010 on 2010-12-07
Thanks. ya'll! That appears to have worked! Xine was just to slow at buffering streaming radio.

---

### Post by karthick87 on 2010-12-07
Mark this thread as [COLOR=Red][SOLVED][/COLOR]

---

### Post by zer010 on 2010-12-08
I can't mark it as [SOLVED]!!!!! 
All it gives me is the option to mark it as [UNSOLVED]!!!!
Whatever shall I do????? :roll:

---

### Post by karthick87 on 2010-12-08
Lol it is already marked as solved.

---

