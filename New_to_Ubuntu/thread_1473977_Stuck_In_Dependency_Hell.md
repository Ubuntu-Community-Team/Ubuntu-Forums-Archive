---
title: "Stuck In Dependency Hell"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by lordofhumankind on 2010-05-05
I just upgraded to Ubuntu 10.04, and like it fine for the most part. However, it dropped support for Awn-Manager. Thinking this shouldn't be an issue, I just go their website to download and install it from there.

However, when I do ./configure, it tells me I need PyGtk. I go to configure this, and get the following:

*** 'pkg-config --modversion glib-2.0' returned 2.22.1, but GLIB (2.23.6)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error: gobject is required to build pygtk?

Additionally, while foolishly looking for answers in Synaptic, I accidentally uninstalled gnome. Now when I go to reinstall it, Synaptic tells me that I need swfdec-mozilla. 

The problem is that when I install that, gnome-desktop-environment is removed. 

The second problem is not so important, as I have back most of what I lost. Just a few things remain a little off. The first can also be avoided by just using a dock still in the repositories. But I'm tired of workarounds and clumsy sweep the dust under the rug fixes.

---

### Post by bodhi.zazen on 2010-05-05
What are you asking for in terms of support ?

Upgrades can go bad with any OS, and IMO you should be prepared to re-install if they go bad.

In terms of compiling AWN , as it is not in the Ubutnu repositories you really should use the AWN forums or mailing list. Of course you can always try to "hack" you way through the compilation and follow the advice of the error message.

In terms of "dust under the rug fixes" I understand what you mean, that can be frustrating, but, keep in mind you are trying to install an un supported application. When doing so you should expect bugs.

That is not the same thing as experiencing a problem with an application from the (main) Ubuntu repositories.

---

### Post by cgroza on 2010-05-05
Why don't you install it from their repo?

---

### Post by cis.ash on 2010-05-05
why dont you install awn manager from the software center ?

---

