---
title: "Firefox address bar fails"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by zmike1 on 2009-06-15
I keep getting an error with firefox that just seems to have come up since the last update:
(I'd show a screenshot but don't know how)
/home/mike/Desktop/Screenshot-Assertion Failed-1.png

Anyway, within the error window there are 16 lines of text:
ASSERT:*** search_installLocation: engine has no file!
stack trace:
ENSURE_Warn:false (installLocation: engine has no file!21475000037
1: ()
2: ()
3: ()
4:epsGetAttr([object Object],alias)
5: ()
...
it goes on for 16 lines...

This only happens when I type an address in the address bar and hit return.  Otherwise Ffox seems to work fine.  Seamonkey works but I'd prefer Ffox.

Any advice?
Thx.

OH.  For what it's worth, I just hit the "manage attachments" button on the Forums web page and got a similar error and managed to paste the test below:  this has only 11 lines:


ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1: ()
2: ()
3: ()
4:epsGetAttr([object Object],hidden)
5: ()
6: ()
7:currentEngine()
8:get_currentEngine()
9:updateDisplay()
10:init()
11: ([object XULElement],6)

---

### Post by lovinglinux on 2009-06-16
It could be a problem with *places.sqlite* file on your profile. Try deleting it (back it up first) and restart Firefox.

---

### Post by SoftwareExplorer on 2009-06-16
I tend to have this happen to me when Firefox is updated while it is running. It goes away for me once I shutdown Firefox completely and then restart it. hope that helps

---

### Post by zmike1 on 2009-06-16
Thank you.  The complete shutdown (of the computer, not just Firefox seems to have worked)
@Lovinglinux, thank you for the idea, I didn't know how/where to find my profile, so I took the easy approach.
Now I just hope I can figure out how to make the thread as solved...
Thank you both!

---

### Post by zmike1 on 2009-06-16
I guess it's marked as solved.
Thanks again.

---

