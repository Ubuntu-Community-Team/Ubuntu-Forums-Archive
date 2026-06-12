---
title: "Firefox: I get question marks instead of websites"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by Kexolino on 2011-04-28
Instead of some webpages, I get this, and it's the same in 3.6.16, 3.6.18, and firefox 4:

[IMG]http://img7.imageshack.us/img7/7109/screenshot2kl.png[/IMG]
 
Question marks all the way. ](*,)
Any ideas why it's like this?

---

### Post by jtarin on 2011-04-28
What language are you are using? You might need to change some settings under Firefox>edit>preferences>content tab.

---

### Post by Kexolino on 2011-04-28
> **jtarin said:**
> What language are you are using? You might need to change some settings under Firefox>edit>preferences>content tab.

I have English (en, en-us; default, I guess?) in languages, but removing one or the other doesn't change anything.

---

### Post by ajgreeny on 2011-04-28
Just to try it out, see what happens if you rename the hidden folder in your home from .mozilla to .mozillabak and start FF again.  It sounds as if your profile has become corrupted.

If that works you can then get back all your bookmarks etc from the .mozillabak folder and save a lot of time reconfiguring, but be careful what you copy back, as somewhere along the line you may end up in the same position.

---

### Post by Kexolino on 2011-04-28
> **ajgreeny said:**
> Just to try it out, see what happens if you rename the hidden folder in your home from .mozilla to .mozillabak and start FF again.  It sounds as if your profile has become corrupted.

If that works you can then get back all your bookmarks etc from the .mozillabak folder and save a lot of time reconfiguring, but be careful what you copy back, as somewhere along the line you may end up in the same position.

Thanks, it worked! Should I delete the .mozillabak folder, or leave it?

---

### Post by ajgreeny on 2011-04-28
> **Kexolino said:**
> Thanks, it worked! Should I delete the .mozillabak folder, or leave it?
If you want your bookmarks back, which may be the most important part of your profile (I would never remember all my bookmarks!), just find the *.mozilla/firefox/qn4bdmr0.default/bookmarkbackups* folder and restore the latest of those *bookmarks-2011-04-28.json* files from the FF **Bookmarks->Organise bookmarks->Import and backup** menu item.  After doing that you can either delete the old one, or just hang on tyo it, just in case any other configuration files or folders for FF are needed later.

PS:  Your profile will be a different alphanumeric to my* **qn4bdmr0**.default.*

---

### Post by lovinglinux on 2011-04-28
> **ajgreeny said:**
> If you want your bookmarks back, which may be the most important part of your profile (I would never remember all my bookmarks!), just find the *.mozilla/firefox/qn4bdmr0.default/bookmarkbackups* folder and restore the latest of those *bookmarks-2011-04-28.json* files from the FF **Bookmarks->Organise bookmarks->Import and backup** menu item.  After doing that you can either delete the old one, or just hang on tyo it, just in case any other configuration files or folders for FF are needed later.

PS:  Your profile will be a different alphanumeric to my* **qn4bdmr0**.default.*

There are also other important stuff like passwords, extensions and so on.

Instead of renaming the profile you could try to find the culprit, so you can keep you personal stuff.

I would begin by starting Firefox in safe mode, since it could be an extension causing the problem or deleting the file *prefs.js*, which holds only the preference stuff.

---

