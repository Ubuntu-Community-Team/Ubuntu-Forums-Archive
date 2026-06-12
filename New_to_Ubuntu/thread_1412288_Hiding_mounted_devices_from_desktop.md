---
title: "Hiding mounted devices from desktop"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by thameera on 2010-02-21
Hello,

When external media are plugged in they're automatically mounted, opened, and an icon is shown in the desktop.

How can I keep automounting option, but stop opening new windows and hide the desktop icons of the media?

Thanks!

---

### Post by mikewhatever on 2010-02-21
To stop a window opening, in the file browser, Edit->Preferences->Media tab, uncheck the 'Browse media when inserted' tab.

To hide the desktop icons, in Terminal, type gconf-editor, navigate to /apps/nautilus/desktop, uncheck the 'volumes_visible' box. This tweak removes all mounted volumes' icons from the desktop.

---

### Post by thameera on 2010-02-21
Thanks, mikewhatever!
It solved the problem.

---

