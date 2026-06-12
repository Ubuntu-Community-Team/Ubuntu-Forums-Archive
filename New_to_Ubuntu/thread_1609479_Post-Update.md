---
title: "Post-Update"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by fslezak on 2010-10-30
After updating GDM, my kernel, and many other things, I am having many problems.

1: My Compiz no longer loads. I have to manually load Compiz from my terminal, then Alt-F2 "compiz --replace" I would like to fix this.

2: I now get a very pesky Accessibility logo in my taskbar.

3: My Copy/Paste will not work between apps. I see the options, and I can copy/paste within an application, but as I said, it will not work between apps.

PLEASE HELP ME!!!!

---

### Post by cariboo on 2010-10-30
Please provide more details, it's pretty hard to help without knowing what graphics adapter you are using.

---

### Post by fslezak on 2010-10-30
I use an Intel Corporation 82852/855GM Integrated Graphics Device (rev 02).

---

### Post by HermanAB on 2010-10-30
Howdy,

You got to read the logs to figure out what is going on.

$ sudo tail -n 1000 /var/log/messages

You have discovered why I never update my systems.  The auto-screw-up is the first feature I disable after installing a Linux system.  I rather re-install once a year, then leave well alone the rest of the year.

---

