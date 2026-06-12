---
title: "Nautilus config?"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by gurt on 2009-07-02
I want to change the default view to "list view". But the changes don't seem to stick if I close and reopen Nautilus. Is there a config file somewhere? nautilus --help is pretty useless and where's the ubuntu nautilus man page?

Ta!

---

### Post by kaibob on 2009-07-02
Have you set the "Default View" in *Edit > Preferences > Views*? This setting should stick from session to session. 

The setting is saved in the GConf Configuration System and can be viewed with the gconf-editor. The applicable key is:

/apps/nautilus/preferences/default_folder_viewer

---

### Post by gurt on 2009-07-02
Thanks kaibob! -- clearly I need to take a break... I'm confusing this install with my last one. :rolleyes:

---

