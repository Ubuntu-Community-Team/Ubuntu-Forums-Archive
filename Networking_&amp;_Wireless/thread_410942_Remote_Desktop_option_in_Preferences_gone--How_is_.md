---
title: "Remote Desktop option in Preferences gone--How is it restored?"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by computerease on 2007-04-16
I am installing VNC using vnc-common and xvncviewer packages (U 6.06LTS).  Hudson et.al. in *Ubuntu Unleashed* says config done through Preferences > Remote Desktop.  That item is not present in my Preferences menu.  How can that item be restored.  I did not, to my knowledge, remove it (and I keep pretty good logs -- with a little help from Syn>)  Please advise.

---

### Post by computerease on 2007-04-16
Life is good.  Solved this one.  the Gnome Remote Desktop application is vino.  It had somehow been removed.  Once it was reinstalled the Preferences > Remote Desktop reappeared and was configurable.  The key was inadvertantly found in a google search for gnome-remote-desktop.  The third entry on the results list presented the call [https://launchpad.net/vino](https://launchpad.net/vino).  A search in Synaptic for vino revealed it was uninstalled.  Re-installation placed it back on the Preferences list.

---

### Post by computerease on 2007-04-16
Life is good.  Solved this one.  the Gnome Remote Desktop application is vino.  It had somehow been removed.  Once it was reinstalled the Preferences > Remote Desktop reappeared and was configurable.  The key was inadvertantly found in a google search for gnome-remote-desktop.  The third entry on the results list presented the call [https://launchpad.net/vino](https://launchpad.net/vino).  A search in Synaptic for vino revealed it was uninstalled.  Re-installation placed it back on the Preferences list.  This issue is resolved.

---

