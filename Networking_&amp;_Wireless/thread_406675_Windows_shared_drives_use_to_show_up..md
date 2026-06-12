---
title: "Windows shared drives use to show up."
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by lawentzel on 2007-04-11
After installing version 7.04 of Ubuntu I was happy to see I could access my home shared drives.  With version 6.10 I was never able to.  Last night, when I needed to access one of the shared drives, they did not show up at all.  I clicked on Places, and Network.  Before, my wifes computer, my computer and the Work Group icon appeared.  Now it is just the Work Group icon.  I am able to print to network printers without any problems.  Just can't see my shared drives.  What's up?  What do I need to do?  Any suggestions would be greatly appreciated.  Thank you all in advance.

---

### Post by Gina on 2007-04-11
Have you installed samba?

---

### Post by lawentzel on 2007-04-11
No.  But then I didn't uninstall Samba either.  So, if it worked before, why doesn't it work now?

---

### Post by lawentzel on 2007-04-14
I have verified that Samba is installed.  In fact, I have reinstalled it, as I couldn't figure out how to restart the services in case that was messed up.  My shared printers on my Windows computers are accessible and very much usable.  Still can't figure out why I was able to view my shared drives before, and suddenly it has stopped.

I have tried the following:

```
smb://wraith
smb://fluffy
```

And get an error indicating they are not available.  Wraith is my computer, Fluffy's my wifes.  I have searched several user groups and websites, but am not having a lot of luck here.

---

