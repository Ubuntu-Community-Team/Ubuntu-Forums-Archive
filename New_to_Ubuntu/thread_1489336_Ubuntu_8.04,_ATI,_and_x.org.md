---
title: "Ubuntu 8.04, ATI, and x.org"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by Stigmata13 on 2010-05-21
Hello. Recently I downgraded to Ubuntu 8.04 LTS, for the simple fact that was the only way I could use the drivers found on ATI's site.
Everything ran fine for a week or so, but now, it seems like my computer won't let me use that driver. I'm starting to think I may have accidentally updated x.org which would explain why, with the driver installed, my computer refuses to boot into ubuntu, and I have to use the recovery option to fix it.
The installer for these drivers say that it will only work with X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, or 7.4
How can I tell which version of X.org I have installed? And, if need be how can I downgrade to a proper version so these drivers will work?

---

### Post by Stigmata13 on 2010-05-21
Bump for justice :(
I googled it and it's telling me i'm running xorg version 11.
I would much appreciate it if someone could tell me how to reinstall xorg and run version 7.4 :(

---

### Post by mrboojive on 2010-05-21
You are definitely not running version 11 of X. X itself is sometimes called X11. Probably that's what you came across. The command for finding what version you have of X is ```
X -version
```
I'm not sure why you think you need to use 8.04, but I think you would probably be better off installing the current version of Ubuntu and just using the restricted drivers manager to get the fglrx ATI driver (essentially, it's the same driver as what you're trying to use from ATI's site).

---

