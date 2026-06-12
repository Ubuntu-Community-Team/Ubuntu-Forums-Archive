---
title: "chrome fatal flaw"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by degarb on 2010-02-01
I installed chrome, like it well. Faster than firefox.  However, there is no way of setting disk cache limit. Or so it appears.  This is a notebook with 6 gig hard drive.  

So, do I simply go snaptic package manager and uninstall it, or is there other garbage that needs removing?

---

### Post by zeroseven0183 on 2010-02-02
Setting disk cache limit is mentioned in this [Chromium thread]("http://code.google.com/p/chromium/issues/detail?id=21677"). Check it out.

Same issue reported with this [Ubuntu thread]("http://ubuntuforums.org/showthread.php?p=8761951")

---

### Post by degarb on 2010-02-04
unfortunately, you missed the boat.  The chromium thread has nothing to do with disk cache.

[http://www.google.com/support/forum/p/Chrome/thread?tid=098d42a41aacdc6d&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=098d42a41aacdc6d&hl=en)

This deals with issue.  But the solution involves launching an exe with -- switches.  I have yet to figure out if linux can do launch switches.   

I was going just uninstall chrome, but hide launchers instead to make dormant until a fix or no.

---

### Post by samantha_ on 2010-02-04
Just launch chromium with the format like...
```

chromium-browser *[switches]*
```
just type the switches exactly the same as they are typed in windows. for example, if -v activatres the vebrose mode and you need to do that,

```

chromium-browser -v
```

---

