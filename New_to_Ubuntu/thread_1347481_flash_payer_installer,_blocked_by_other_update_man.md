---
title: "flash payer installer, blocked by other update management software"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by fchartier on 2009-12-06
Hi all, 

I am trying to install the plugin for adobe flash player but i get an error message saying that i need to close first other update management sofware, update manager, aptitude, synaptic

how do u close them, (i havent started them so i assume they start by default)

cheers and thanks

---

### Post by efflandt on 2009-12-06
What were you doing immediately before that, and is anything else that updates or installs minimized at the bottom (maybe you opened 2 copies of Synaptic)?  If you pick Synaptic or Update Manager from the menu, just single click and wait.  If you double clicked, you may have opened 2 copies on top of each other.

I don't think Update Manager appearing minimized with automatic updates should interfere.  But if you are trying to install something else, you may want to close Update Manager, install whatever, then run Update Manager in case there are any updates for what you just installed.

Some package installations initiate deferred processes, so something that appeared to be finished may have still been doing something in the background.

---

