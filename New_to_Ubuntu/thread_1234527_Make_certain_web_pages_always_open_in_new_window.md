---
title: "Make certain web pages always open in new window?"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by InfectedWithDrew on 2009-08-08
I'm trying to find a way to make Firefox load certain pages, like GMail, in a new window whenever I access them.

Can I do this via extension or configuration?  Greasemonkey, perhaps?

---

### Post by asmoore82 on 2009-08-08
middle-clicking, or "wheel-clicking" on modern mice, on bookmarks or links will make them open in a new tab.

---

### Post by InfectedWithDrew on 2009-08-08
> **asmoore82 said:**
> middle-clicking, or "wheel-clicking" on modern mice, on bookmarks or links will make them open in a new tab.

New tab != new window.

---

### Post by Cato2 on 2009-08-08
Try ```
firefox -no-remote -P myprofile
``` - runs a new instance of Firefox.  To begin with, omit the myprofile and it should let you create a new Firefox profile.

This runs a new instance of Firefox so it will be in a new window.  However, it won't share your bookmarks unless you install Xmarks to sync from your main profile - best to view this as a 'web app runner' Firefox.

This command is also handy if you want to log in to the same Ubuntu PC multiple times as the same user - e.g. if you have an much older PC somewhere (say 128 MB RAM only) that's acting as an X terminal into your main PC as it's too slow to run Ubuntu itself.

See firefox --help for more options.

---

### Post by InfectedWithDrew on 2009-08-09
> **Cato2 said:**
> Try ```
firefox -no-remote -P myprofile
``` - runs a new instance of Firefox.  To begin with, omit the myprofile and it should let you create a new Firefox profile.

This runs a new instance of Firefox so it will be in a new window.  However, it won't share your bookmarks unless you install Xmarks to sync from your main profile - best to view this as a 'web app runner' Firefox.

This command is also handy if you want to log in to the same Ubuntu PC multiple times as the same user - e.g. if you have an much older PC somewhere (say 128 MB RAM only) that's acting as an X terminal into your main PC as it's too slow to run Ubuntu itself.

See firefox --help for more options.Any solution that will work in Windows as well?

---

