---
title: "Font paths?"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by nathan28 on 2011-04-20
Stupid question, but what files do I alter to add a directory to the paths searched for fonts (i.e., by fc-cache)? I use multiple distros and logins and want to avoid gobbling up disk space. I read that sym-linking will work, so

> ln -s /datapartition/FontsForAll ~/.fonts/symlinkfonts
(and/or)
ln -s /datapartition/FontsForAll /usr/share/fonts/sy

across all users should work b/c fc-cache crawls subdirectories, right? But there's a file that stores these paths, rights?

And presumably I could do the same w/ icons, themes and other tweak/shared material that might go in /usr/share?

---

