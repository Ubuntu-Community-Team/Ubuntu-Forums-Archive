---
title: "Dsktop problems"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by Gop-Stop on 2009-09-18
I have problems with my folders. I deleted my desktop folder in homefolder, after that my homefolder files and folders started placed in the desktop. I can't find where I may change directory. Can help me someone?

---

### Post by wojox on 2009-09-18
You need to open Places > Home Folder.

Then View > Hidden Files.

Open .config > user-dirs.dirs

Add: XDG_DESKTOP_DIR="$HOME/Desktop"

Restart.

---

### Post by Gop-Stop on 2009-09-18
Thanks

---

