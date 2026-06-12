---
title: "[SOLVED] Firefox automatically offline"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by shortylonglegs on 2008-08-17
My network didn't quite work (dropped connections or not assigning IP) when I used the nm-applet, so I just made a script to connect manually.  The only problem I'm having now is that every time I start Firefox, it is automatically in offline mode.  I've looked, but can't find any option to prevent this, even in about:config as far as I can tell.  Any ideas?

---

### Post by dmizer on 2008-08-17
Open Firefox. Click "file", and uncheck "Work offline" ;)

---

### Post by shortylonglegs on 2008-08-17
Thanks, but I would really like a way that I wouldn't have to do that every time I start Firefox, because I frequently open several tabs before looking at the window.  That requires me to uncheck "work off line" and then reload every page.  That got tedious very quickly.

---

### Post by dmizer on 2008-08-17
> **shortylonglegs said:**
> Thanks, but I would really like a way that I wouldn't have to do that every time I start Firefox, because I frequently open several tabs before looking at the window.  That requires me to uncheck "work off line" and then reload every page.  That got tedious very quickly.

I see.  This is apparently a bug.  Here is the discussion thread: [http://support.mozilla.com/tiki-view_forum_thread.php?locale=en-US&forumId=1&comments_parentId=60433](http://support.mozilla.com/tiki-view_forum_thread.php?locale=en-US&forumId=1&comments_parentId=60433)

Here's the bug report: [https://bugzilla.mozilla.org/show_bug.cgi?id=339814](https://bugzilla.mozilla.org/show_bug.cgi?id=339814)

Here is a posted workaround:
> open firefox
key in about:config in url bar
Set toolkit.networkmanager.disable to true

My google search was -> firefox starts "work offline"

---

### Post by shortylonglegs on 2008-08-18
Thanks, that worked.

---

