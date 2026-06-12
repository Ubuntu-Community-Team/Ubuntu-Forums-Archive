---
title: "Troubles compiling gnome-ppp 0.3.22"
date: 2005-06-23
forum: Networking &amp; Wireless
---

### Post by renoir98 on 2005-06-23
I'm trying to compile and install gnome-ppp 0.3.22 from sources since i haven't found a .deb package to use.
I run the ./compile command but in the end it outputs this error:
```

checking for gtk+-2.0 >= 2.4.0 libglade-2.0 >= 2.4.0... Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found

configure: error: Library requirements (gtk+-2.0 >= 2.4.0 libglade-2.0 >= 2.4.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```
Can anybody help me understand where the problem resides?
Shall i install additional packages?
I'm on a default Hoary installation.
Thanks in advance to all.

---

### Post by tristan on 2005-06-23
Hmm, I had no trouble installing gnome-ppp via synaptic, which was a hell of a lot easier than trying to comile it (I never had any luck building it on my old Mandrake box). Maybe you need to have a look at what repositories you have enabled.

---

### Post by renoir98 on 2005-06-23
You're right,the most recent version available via apt repositories is 0.3.21
(located in the backports mirrors) but version 0.3.22 finally provides multiple providers support,a major improvement.
Any suggestions?

---

### Post by tristan on 2005-06-23
I'd say you need the gtk2 development files, I think they'll be available via synaptic too. Knowing how tricky it is to compile gnome apps, you'll probably need a few others as well, and will only find out as you install each one and type ./configure.

---

