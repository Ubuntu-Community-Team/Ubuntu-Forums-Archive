---
title: "relatime and removable USB hard drives"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-08-23
When mounting a drive, by default Linux records every single access to a file. Naturally, this is inefficient and reduces the life of the drive.

You can specify the option *relatime*, which records prevents this repetition.

According the [Ubuntu fstab documentation]("https://help.ubuntu.com/community/Fstab#Options"), "Ubuntu 8.04 now uses relatime as default for linux native file systems."

What I want to know is whether this is simply because the installation puts *relatime* into [COLOR=DarkRed]/etc/fstab[/COLOR] (I can see that it's there), or is *relatime* automatically applied to other mounted drives such as removable USB drives?

If it's only via [COLOR=DarkRed]/etc/fstab[/COLOR], then I must put my removable USB drive (formatted as ext3) into [COLOR=DarkRed]/etc/fstab[/COLOR] with *relatime*, shouldn't I?

Is there a way to tell whether a mounted drive has the *relatime* option applied?

---

