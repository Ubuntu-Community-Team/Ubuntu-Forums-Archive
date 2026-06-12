---
title: "Chromium issues!!"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2010-07-19
All my browsing history, passwords, and bookmarks were deleted.  Now it won't remember anything.  Even a current log in.  I log in, and it immediately logs me out.  I've un installed and re installed via Software Centre, but nothing has changed.  Currently using swiftfox, but really want my Chromium back.

---

### Post by new__buntu on 2010-07-19
If you go to /opt is there still a google directory?

---

### Post by TriBlox6432 on 2010-07-19
There are no directories actually.

---

### Post by new__buntu on 2010-07-19
Well, that's quite different from my chrome installation. Do you still have your ~/.config/google-chrome directory (that's where my chrome config files were, yours may be in a differently named file)? I'm guessing that your old config files did something to screw with chrome, so if you clear those out and then reinstall chrome you should theoretically get functionality back. I think.

---

### Post by TriBlox6432 on 2010-07-22
I can't seem to find that directory...  I'm sorry.  *headdesk*

---

### Post by ankspo71 on 2010-07-22
Hi,
Look in /home/YOURNAME/.config/chromium/Default/ for a file called "Bookmarks" and possibly a file called "Bookmarks.bak". The .config folder is a hidden folder in your home folder. 
Hope this helps.

---

