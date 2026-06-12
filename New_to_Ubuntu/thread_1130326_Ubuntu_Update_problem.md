---
title: "Ubuntu Update problem"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by Autumnie88 on 2009-04-19
So, I have never used anything but Windows, so I am struggling a bit today.  I have had this Dell mini for a few months and have had no problems with ubuntu.  Today, I installed the updates, but there were quite a few of them and the computer went into hibernation mode or something and now it tells me there was an error while installing it.  Now, I cannot even find the network option to try to get online to finish installing the updates.  Anyone have any idea how I can fix this?

---

### Post by drs305 on 2009-04-19
Try running the following  - it is one of the common error fixes. 

```

sudo apt-get install -f
```

We really need to know the specific error message(s) if you can provide them.

---

### Post by halitech on 2009-04-19
are you now unable to get online with the machine? maybe 1 of the updates was for the wireless (I'm guessing at this) and it has knocked out your connection.

---

### Post by Autumnie88 on 2009-04-19
I am assuming that is what happened, but I don't know how to fix it.  I know NOTHING of ubuntu, so I don't know how to run the error code.

---

### Post by Monotoko on 2009-04-19
From the top menu, you go: Applications -> Accessorys -> Terminal

A window will come up, place that code in that window

---

### Post by Autumnie88 on 2009-04-19
Thanks!  Got that, but now it says dpkg was interrupted you must manually run 'dpkg --configure -a' to correct the problem.  Sorry if I seem like an idiot, but I have no idea what that means.

---

### Post by halitech on 2009-04-19
open a terminal and type in
```
dpkg --configure -a
```

---

### Post by Autumnie88 on 2009-04-19
I put that in and it tells me that the requested operation requires superuser priviliges.  Again, sorry if I sound like an idiot, but I have no idea how to get those priviliges.

---

### Post by halitech on 2009-04-19
sorry, should have been
```
sudo dpkg --configure -a
```

---

### Post by Autumnie88 on 2009-04-19
Okay, so I have done all of that, and now it tells me that a package was automatically installed and needs to be removed, so I run what it tells me to, but then it tells me that it cannot resolve dell-mini.archive.anonical.com.  It says it is unable to fetch some archives.  Any ideas?

---

### Post by Jimlas53 on 2009-04-19
Go to >System >administration >software sources. Click on Third-Party Software tab.  Take a look at the list for the Dell reference.  I think the web address is borked, it should be 
dell-mini.archive.canonical.com/
your reference is listed as dell-mini.archive.anonical.com/
Select Edit and correct the address, if this is the problem you should be able to get the repository you need.

Hope this helps!

-Doug

---

### Post by Autumnie88 on 2009-04-19
Unfortunately, that was just my typo.  It is in there as you said it should be!  Any other ideas?

---

### Post by halitech on 2009-04-20
the address works for me in a web browser. what package is it saying it needs to remove?

---

### Post by mikechant on 2009-04-20
You said your wireless connection was knocked out by the failed update - have you got a wired connection running instead as a temprorary measure? If not, that's probably why you're get the 'cannot resolve', 'unable to fetch' etc. messages.

---

