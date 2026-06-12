---
title: "&quot;Guest session&quot; desktop problem"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by mvalviar on 2009-02-04
Sorry if this question has already been solved. I'm having no luck finding it. 

Whenever I switch to a guest session the desktop doesn't look good. I believe that it should be the default human theme because the background is the default ibex. But it doesn't look good. Whenever I try to correct it through the appearance menu there appears a pop up saying:

```
Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.
```

How can I fix this? Thanks in advance.

---

### Post by vikramaditya on 2009-02-04
lifted from [this]("http://ubuntuforums.org/archive/index.php/t-579167.html") source . . .

> Go to: System -> Administration -> Synaptic Package Manager (this requires your password).
- Either search for dbus or scroll down to it and click on the left hand square. 
- A menu appears, 
- Select the Reinstallation option.
- Click the Apply button at the top of the screen.
- Restart your machine.

If this doesn't work for you, then it may be time to edit config files.
Happy hunting!

---

### Post by mvalviar on 2009-03-21
I tried what was mentioned above. It didn't work. Is there a config file for the guest session? If so where is it?

---

### Post by mvalviar on 2009-03-22
*bump*

---

