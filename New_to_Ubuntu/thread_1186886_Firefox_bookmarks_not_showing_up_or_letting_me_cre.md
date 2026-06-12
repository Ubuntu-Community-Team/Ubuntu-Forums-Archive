---
title: "Firefox bookmarks not showing up or letting me create"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by drunkmatador on 2009-06-13
I am using Firefox 3.0.7 on Ubuntu Hardy Heron and have been having this problem for a long time.. in fact ever since installing Firefox. My bookmarks don't show up whatsoever.. when I click on Bookmark This Page, nothing happens.

When going to Organize Bookmarks the window opens, but there are no bookmarks to be shown.

Any ideas how I can get this working? I've just been avoiding using bookmarks but it's really starting to get to me having to sort through google results to find pages I'd normally have bookmarked.

---

### Post by mgranet on 2009-06-14
That's odd. It almost sounds like a permissions problem. Did you install firefox from the repos, or from the website?

---

### Post by drunkmatador on 2009-06-14
repos.

---

### Post by mgranet on 2009-06-14
You might try going into synaptic, right clicking on firefox, then selecting purge. This will wipe all settings. After you purge it, re-install and see if that corrected it.

---

### Post by lovinglinux on 2009-06-14
There is no need to reinstall, just delete the file *places.sqlite* from your Firefox profile folder. This is a common issue related to a corrupted *places.sqlite* file.

Your Firefox profile is located at ~/.mozilla/firefox/

---

### Post by drunkmatador on 2009-06-14
Thanks a lot! Works fine now.

---

