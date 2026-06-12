---
title: "xine + xine-based applications not sharing"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by soapBAR2 on 2009-01-02
This may be the wrong place for this, but I'm still an absolute beginner so I'll post here ;)

Xine doesn't allow two (or more) programs to use the xine decoder simultaneously. For example, playing a music file in Amarok and then trying to open a movie file in Kaffeine (without stopping Amarok playback) will result in the movie file being played with sound. As far as I'm aware, this problem is limited to xine, as VLC and system sounds will play alongside xine-based programs.
[B]
How do I allow xine to be used by more than one file at once[/B] - or alternatively, how do I stop anything xine-based from locking up when attempting to open a file when xine is busy?

I know this is fixable by being careful not to open two files at once, but it's easy to open a youtube link/etc without thinking to stop music playback first (especially if it's paused). The problem usually ends with having to restart the X server (the system becomes almost entirely unresponsive, making it difficult to get to a shell to kill the playback), and it's a pain to lose all my unsaved work because of one oversight.

System info: KDE / Ubuntu 8.04

Thanks in advance.

---

### Post by igknighted on 2009-01-02
Is that KDE3 or KDE4?

EDIT: And youtube uses flash, which should have nothing to do with Xine, so perhaps xine isn't the issue.  Sound from multiple apps has long been known to be an issue though...

---

### Post by chrisod on 2009-01-02
The sound not working from multiple apps issue is probably a Pulse Audio issue.

---

