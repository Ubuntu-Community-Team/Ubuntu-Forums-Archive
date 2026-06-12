---
title: "How can I get file admin privileges in Ubuntu 10.4 File Manager?"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by GregA on 2010-05-06
Hi - - I can't recall the package to install, that allows either Nautilus or the alternate Ubuntu file manager to have "change" rights for files (without requiring the terminal window and command line) . . . . thanks.

---

### Post by 3rdalbum on 2010-05-07
The package is "nautilus-gksu". You can install it from Synaptic, and when you next log in, you'll be able to right-click a file or folder and choose "Open as Administrator".

---

### Post by aysiu on 2010-05-07
Alternatively, you can create a launcher or keyboard shortcut for the command ```
gksudo nautilus
```

---

### Post by GregA on 2010-05-07
Thank you both! . . . . I'll implement each suggested solution.

---

