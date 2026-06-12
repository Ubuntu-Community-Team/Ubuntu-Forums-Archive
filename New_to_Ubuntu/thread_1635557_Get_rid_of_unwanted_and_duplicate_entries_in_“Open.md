---
title: "Get rid of unwanted and duplicate entries in “Open With” dialog"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by karthick87 on 2010-12-02
I know that i can delete it manually from **[B]~/.local/share/applications** [/B] but how to avoid getting these duplicate entries in future?Also is there way to automatically regenerate the list so that the duplicate entries will be removed.

---

### Post by Liverbones on 2010-12-02
Unfortunately, I'm not sure of how to do this automatically, nor do I know how to automatically regenerate the list of applications; however, there is an easier way to remove applications manually than editing the .desktop files in your home folder.

You can right-click on any file in Nautilus and select Properties. From the Properties dialog, you can select the Open With tab, and add or remove entries for that particular file type.

I doubt that that was useful, considering the information that you requested, but honestly, this is something that would interest me, as well. Simply thought that I would offer another way of accomplishing the task manually. :)

**EDIT:** Just thought of something that may be useful; you might be able to configure which applications open what files by editing the mimeinfo.cache file. That's located in /usr/share/applications/mimeinfo.cache. Might work out well for you.

---

