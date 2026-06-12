---
title: "Gedit plugin can't find gedit/pygtk"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by Halfling Rogue on 2009-11-11
I'm trying to install the [Gedit Developer Plugins package]("https://launchpad.net/gdp") so that I can have multiple file search/replace functionality, but I'm running into some configuration problems.

When I try to configure the plugin in the terminal, I get this error:

```
checking pkg-config is at least version 0.9.0... yes
checking for GEDIT... configure: error: Package requirements (
    pygtk-2.0 >= 2.14
    gedit-2.20 >= 2.26.0
) were not met:

No package 'pygtk-2.0' found
No package 'gedit-2.20' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GEDIT_CFLAGS
and GEDIT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

Thing is, my Gedit is version 2.22.3, and I have pygtk-2.0 (if locate is to be believed), so my machine does fulfill the requirements. They're both nestled safely in /usr/share, which I'm pretty sure is where they're supposed to be. I check pkg-config just to be sure, and get this:

```
$ locate pkg-config
/usr/bin/pkg-config
/usr/share/doc/pkg-config
/usr/share/doc/pkg-config/AUTHORS
/usr/share/doc/pkg-config/NEWS.gz
/usr/share/doc/pkg-config/README
/usr/share/doc/pkg-config/changelog.Debian.gz
/usr/share/doc/pkg-config/changelog.gz
/usr/share/doc/pkg-config/copyright
/usr/share/man/man1/pkg-config.1.gz
/var/lib/dpkg/info/pkg-config.list
/var/lib/dpkg/info/pkg-config.md5sums
```

Not quite sure what the problem is here. Do I need to add /usr/share to the pkg config path?

(Proof that using Linux for almost six years does not prevent me from being an utter n00b sometimes. I tried Googling the problem, but no one seems to have this particular issue.)

---

### Post by falconindy on 2009-11-11
Is there a reason you've chosen to compile from source rather than use the PPA listed on the page you linked?

---

### Post by Halfling Rogue on 2009-11-12
They only seem to have PPAs for Jaunty and Karmic. I'm using Hardy.

---

