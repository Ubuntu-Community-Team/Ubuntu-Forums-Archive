---
title: "installing software (gtk and glib trouble)"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by LiamG on 2009-06-25
I'm trying to install some new programs onto ubuntu, but the configure command won't finish because it says that I don't have glib / gtk installed.

Eg:

```
Can't find libraries (or headers) of "gtk+".
  Fetch it from <URL:ftp://ftp.gtk.org/>
```


From doing a little research, it would seem that glib / gtk are fairly fundamental and I probably do have them installed. How can I either get my computer to recognise them or reinstall them?

Thanks in advance.

---

### Post by taavikko on 2009-06-25
When compiling from sources, you need to have the correct package-dev files installed, example gtk needs "libgtk2.0-dev" package installed.

And you'll probably need the software to compile the software, check for the package "build-essential"

Hope this helps in you in any way.

---

