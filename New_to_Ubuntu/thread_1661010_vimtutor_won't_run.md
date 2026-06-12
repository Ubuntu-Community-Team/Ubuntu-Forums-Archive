---
title: "vimtutor won't run"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by mucor49 on 2011-01-06
Hi, new to the forum, searched previous threads. I have 10.10 and unable to start vimtutor. I have vim. tried 'apt-get install vim-runtime' but when I enter 'vimtutor' as command, vim opens but no tutor. uninstalled>reinstalled vim-runtime, no luck. Tried 'apt-get install vim-full' and receive error message "unable to locate package".
 
In my GUI, admin>syanptic pkcg mgr, it shows: vim-runtime, vim-common, vim-tiny, -dbg, -gui common, and -gnome, as installed on my system. Please make a suggestion.
 
A year ago, two previous versions of Ubuntu, when I only had vi, I could run vimtutor. Now I want to 'brush up' on the features with the tutor.
thanks,
mucor49:confused:

---

### Post by gmargo on 2011-01-06
If you have **vim-gnome** installed, then the tutor should work. If not you could install that or the **vim-gtk** package. (The problem is that by default only the **vim-tiny** package is installed, which is a small, limited version.)

---

### Post by mucor49 on 2011-01-06
Thank you gmargo!   Didn't realize I "lied" when I said I had vim-gnome.  Installed it and the vim tutor popped right up.):P
mucor49

---

