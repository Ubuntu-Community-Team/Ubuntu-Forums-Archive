---
title: "web browser hiden link?"
date: 2014-06-09
forum: Networking &amp; Wireless
---

### Post by frank18 on 2014-06-09
Hi guys;i'm not getting the browser link search in this E-machines intel  celeron D in xubuntu 14.04 the same way i get in another pc intel P4. 
see pic there is a black bar in place of the link http/www.  compare to a good same ops firefox browser.
never seen this!

---

### Post by bapoumba on 2014-06-09
[http://ubuntuforums.org/showthread.php?t=2221850](http://ubuntuforums.org/showthread.php?t=2221850)
Although for Firefox, you pic does look the same.
Please see the last post in the thread.

---

### Post by frank18 on 2014-06-10
> **bapoumba said:**
> [http://ubuntuforums.org/showthread.php?t=2221850](http://ubuntuforums.org/showthread.php?t=2221850)
Although for Firefox, you pic does look the same.
Please see the last post in the thread.

Thanks bapoumba for your info,it's exactly same issue, and if it's not the same pic in my attachment is because it's one was taken from another pc where the web browser in firefox29 Xubuntu 14.04 is working good and the other is taken from the pc that has the black bar hiding the links also running same  xubuntu 14.04 and firefox 29.

now the last page you suggested has this suggested code to use in the firefox start up page 

''about:config

gfx.xrender.enabled;**false**

all i could get was delete all my favourites and stuff in the history and problem still there.

unless you suggest anything else in the last page i'm stuck with same issue,thanks in advance

---

### Post by bapoumba on 2014-06-10
You need to enter about:config in the url bar (maybe copy/paste from this thread) and find the gfx.xrander.enabled and change the value to false. In my screenshot, mine is true but does not give any issue. If it does not work, you can always revert it.

---

### Post by frank18 on 2014-06-10
> **bapoumba said:**
> You need to enter about:config in the url bar (maybe copy/paste from this thread) and find the gfx.xrander.enabled and change the value to false. In my screenshot, mine is true but does not give any issue. If it does not work, you can always revert it.

Thanks bapoumba; i was able to fix the issue with your great help,now it's working thanks.

---

### Post by bapoumba on 2014-06-10
Ah, glad to see it's working :)
Please mark your thread as solved, thanks !

---

