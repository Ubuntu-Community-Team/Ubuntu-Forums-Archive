---
title: "Cannot Login"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by tlcmd on 2010-01-29
Me again!
1.4 GHz Athlon, 320 G partitioned HD with Windows XP and Ubuntu 9.10.

Cannot login. When I go to the recovery mode, I can get in by using "startx", but am in the safe more (1 user) Suspect my config files are messed up.

After downloading Ubuntu 9.10, I deleted all of the games; I did have to authenticate to remove "Mines" (a gnome game(?)).
Downloaded Musescore .96 (pre-release version).
Downloaded Avast anti-virus (for Linux)
Copied my music files (mp3, ogg vorbis) from Windows Partition to Ubuntu.

Where do I go from here to repair or replace my config files?

---

### Post by cariboo on 2010-01-29
So you can log in, but you are running the Desktop in failsafe mode, or you running the desktop as root? Startx takes you directly to the desktop with out starting gdm, so there is no login needed to get to the desktop.

If you are running nvidia graphics you can run:

```
nvidia-xconfig
```

from the root prompt in recovery mode. You should then be able to type exit and select resume from the menu.

---

### Post by tlcmd on 2010-01-29
> **cariboo907 said:**
> So you can log in, but you are running the Desktop in failsafe mode, or you running the desktop as root? Startx takes you directly to the desktop with out starting gdm, so there is no login needed to get to the desktop.

If you are running nvidia graphics you can run:

```
nvidia-xconfig
```

from the root prompt in recovery mode. You should then be able to type exit and select resume from the menu.

Thanks,
Will give it a try.
Dick

---

