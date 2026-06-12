---
title: "Firefox not functioning"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by echo314 on 2009-04-23
Don't remember doing anything...just happened while browsing. Cant open a URL if I type it in, but I can if its already a link on a page or from bookmark. If I type in a URL I get 

ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],alias)
5:()
6:SRCH_SVC_getEngineByAlias(slashdot.org)
7:getEngineByAlias(slashdot.org)
8:getShortcutOrURI(slashdot.org,[object Object])
9:([object KeyboardEvent])
10:anonymous(textentered,[object KeyboardEvent])
11:fireEvent(textentered,[object KeyboardEvent])
12:onTextEntered()

---

### Post by azurehi on 2009-04-23
I am using xp while I download 9.04 final and had the same problem.  [http://support.mozilla.com/en-US/kb/Cannot+connect+after+upgrading+Firefox](http://support.mozilla.com/en-US/kb/Cannot+connect+after+upgrading+Firefox)  This corrected the problem for me; I use zonealarm free when in windoz.  Hope this helps.

---

