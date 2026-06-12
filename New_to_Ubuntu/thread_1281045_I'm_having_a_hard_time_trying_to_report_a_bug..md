---
title: "I'm having a hard time trying to report a bug."
date: 2009-10-02
forum: New to Ubuntu
---

### Post by ikisham on 2009-10-02
Hi, brothers and sisters.
I've just installed karmic beta1, run the "System Testing", entered the email address I use to log at Launchpad and received this error message:
> Error: Required fields not contained in POST data: submission_key, system
It's the same if I'm logged in or out at Launchpad. So I can't send the testing report.

So I tried to file a bug against it but I just can't figure how to do it.
I ran ```
xprop WM_CLASS
``` at the Terminal and clicking on "System Testing" window returned ```
WM_CLASS(STRING) = "--log-level=debug", "--log-level=debug"
```

---

### Post by boblemur on 2009-10-02
first:

try loging into [launchpad ]("https://launchpad.net/ubuntu") if that works then do the following:

```
alt + f2
ubuntu-bug checkbox
```

and this will report an error about the package checkbox which is the system testing program.

i hope iv understood your post correctly if not please correct me

---

### Post by ikisham on 2009-10-03
Thank you. I didn't know its package was *checkbox*. So I've added myself to the respective bug in Launchpad.

---

