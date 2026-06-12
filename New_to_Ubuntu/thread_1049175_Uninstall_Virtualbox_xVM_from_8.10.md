---
title: "Uninstall Virtualbox xVM from 8.10"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by Niphoet on 2009-01-24
I've been using Ubuntu for about 2 weeks and I'm loving every minute of it.  I want to UnInstall Virtualbox xVM, but I don't see it listed in the "Add and Remove" where everything else is listed.  I originally downloaded the Ubuntu x32 file from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) and installed it.

Any help on this would be appreciated.

--The Niphoet

---

### Post by mikewhatever on 2009-01-24
Well, I suppose, since you downloaded it from an external source, and not from the repositories, it isn't listed in the Add/Remove. Even though, the package should appear in Synaptic, and you can uninstall it from there, or use the CLI.

---

### Post by diablo75 on 2009-01-24
You might try (in Terminal):

```
sudo dpkg -r virtualbox*
```

---

