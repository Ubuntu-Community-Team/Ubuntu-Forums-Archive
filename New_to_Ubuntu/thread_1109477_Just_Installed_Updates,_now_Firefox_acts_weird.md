---
title: "Just Installed Updates, now Firefox acts weird"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by Teasdale on 2009-03-28
When I open Firefox or highlight and copy any text, I get a box that says the following:

ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0: ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1: ( )
2: ( )
3: ( )
4:epsGetAttr([object Object],hidden)
5: ( )
6: ( )
7: currentEngine ()
8: ( )
9: CM_initMenu([object XULElement],[object XULElement])
10: nsContextMenu([object XULElement],[object XULElement])
11: onpopupshowing([object MouseEvent])

---

### Post by fly-by-night on 2009-03-28
[http://ubuntuforums.org/showthread.php?t=993989&highlight=ASSERT%3A+Search%3A+_installLocation%3A+engine+file](http://ubuntuforums.org/showthread.php?t=993989&highlight=ASSERT%3A+Search%3A+_installLocation%3A+engine+file)

Hope this help.  If not use some of the words from the error to search here on the forum.  You are one of many with same "problem".

---

### Post by Teasdale on 2009-03-28
Thank you - I did a search and found that it was as easy as restarting Firefox. How embarrassing!

---

