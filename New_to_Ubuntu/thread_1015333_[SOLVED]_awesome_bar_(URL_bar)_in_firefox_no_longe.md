---
title: "[SOLVED] awesome bar (URL bar) in firefox no longer works (&amp;quot;engine has no file&amp;quot; error"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by hanzj on 2008-12-18
Hello, 
My ubuntu box upgraded automatically to the newest version of Firefox in the repository.

The installed version of firefox package and firefox-3.0 package, according to Synaptic, is 3.0.5+nobinonly-0ubuntu0.8.10.1.



When I type anything into the URL bar (awesomebar), I get a window that pops-up  saying:

> ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],alias)
5:()
6:SRCH_SVC_getEngineByAlias([http://google.com](http://google.com))
7:getEngineByAlias([http://google.com](http://google.com))
8:getShortcutOrURI([http://google.com](http://google.com),[object Object])
9:canonizeUrl([object KeyboardEvent],[object Object])
10:handleURLBarCommand([object KeyboardEvent])
11:anonymous(textentered,[object KeyboardEvent])
12:fireEvent(textentered,[object KeyboardEvent])
13:onTextEntered()
14:handleEnter(false)
15:onKeyPress([object KeyboardEvent])
16:onxblkeypress([object KeyboardEvent]) In the example above, I typed in "google.com". Please advise.

---

### Post by flanagan on 2008-12-18
You might check to see if the following thread helps; especially the bit about creating a new profile.

[http://forums.mozillazine.org/viewtopic.php?f=23&t=892085](http://forums.mozillazine.org/viewtopic.php?f=23&t=892085)

---

### Post by hanzj on 2008-12-18
actually, i think it had to do with my installing beta versions. I had thought that installing beta versions of firefox would not at all interfere with my current / stable installation of fx. Anyway removing the folders which had the files extracted from the tar.gz files solved the problem.

So I'm marking this thread solved.

---

