---
title: "how to check if update-manager really works?"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by werty2010 on 2011-05-01
i tried some servers before posting this.
when im checking for updates i have the impression that i doesn't really check for them...
it says in the status bar that it downloads 0 bytes...

some help to check if it is really working or not?

---

### Post by mr_luksom on 2011-05-01
You can check it from the terminal, type:

```

sudo apt-get update

```

It will go through the servers checking for updates, and will tell you if it is connecting.

From experience, update-manager is flawless, and matches the equivalent terminal command to update:
```

sudo apt-get upgrade

```

---

