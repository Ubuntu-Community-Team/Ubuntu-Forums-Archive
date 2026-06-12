---
title: "Is copy/paste of /home good enough for a solid backup?"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by tahitiwibble on 2009-01-24
Is copy/paste of the "home" folder from the "File System" G.U.I to an external HD good enough for a solid backup?

Thanks for your thoughts.

[IMG]http://i221.photobucket.com/albums/dd79/wibble_01/Screenshot---FileBrowser.png[/IMG]

---

### Post by maybeway36 on 2009-01-24
I would make a tar/gz or tar/bz2 file to make it smaller, but that's up to you. Just make sure permissions are preserved.

---

### Post by tahitiwibble on 2009-01-24
Thanks maybeway36 ........... just how does one make sure permissions are preserved?

---

### Post by emarkd on 2009-01-24
It really depends on what you want to preserve.  Clearly all of your documents and such are there, as are the configuration files for the apps that you use.  Missing are the system-wide configuration stuff, including Xorg settings, boot menu stuff, settings for any services you run, like samba, mysql, apache, php, etc.  Most of those are in /etc, but again some are in /boot and /var

---

### Post by tahitiwibble on 2009-01-24
> **emarkd said:**
> It really depends on what you want to preserve.  Clearly all of your documents and such are there, as are the configuration files for the apps that you use.  Missing are the system-wide configuration stuff, including Xorg settings, boot menu stuff, settings for any services you run, like samba, mysql, apache, php, etc.  Most of those are in /etc, but again some are in /boot and /var

Thanks emarkd ........ just "home" will suit my purposes. Knowing the other stuff is good too. :)

........... just how does one make sure permissions are preserved?

---

