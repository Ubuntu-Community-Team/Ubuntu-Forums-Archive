---
title: "Help please!!!"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by mhenry on 2009-12-22
I need help on installing the desktop version from the server version. I need to be able to use it as desktop not as a server.

Please Help...:)

---

### Post by nerdy_kid on 2009-12-22
sudo apt-get install ubuntu-desktop

---

### Post by audiomick on 2009-12-22
+1
> **nerdy_kid said:**
> sudo apt-get install ubuntu-desktop

The server and the desktop version are in most respects the same. The command will install the desktop for you, then you will have, for all intents and purposes, a desktop install. You may have to then install things like open office and evolution. I don't know if they are included in the server version.

---

### Post by llawwehttam on 2009-12-22
I'm just wondering what was wrong with the ubuntu-desktop version in the first place. Why install the desktop version form the server version?

---

### Post by Paqman on 2009-12-22
> **audiomick said:**
> +1
You may have to then install things like open office and evolution. I don't know if they are included in the server version.

The package [ubuntu-desktop]("http://packages.ubuntu.com/karmic/ubuntu-desktop") is a meta-package. All it does is depend on all the normal Gnome desktop packages, such as xorg, open office, firefox, evolution, etc. So installing it will drag them all in as dependencies.

If you're no longer using any server packages that you installed then uninstall or disable them. They're a potential security risk on a desktop machine.

---

