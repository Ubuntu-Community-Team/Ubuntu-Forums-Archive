---
title: "trouble with Flash in Firefox"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by the big e on 2010-06-16
Flash question; 
Flash is insensitive to clicking on buttons. Some clicks register but clicks on buttons don't, apparently.

(Firefox on Lucid Lynx installed with Wubi on a thinkpad with windows xp.)

Should I install a different plugin or change some settings or what?

---

### Post by ubunterooster on 2010-06-16
Go to Tools>addons in firefox. What does shockwave flash show as its version?

Mine says 10.0 r45

---

### Post by oldsoundguy on 2010-06-16
> **ubunterooster said:**
> Go to Tools>addons in firefox. What does shockwave flash show as its version?

Mine says 10.0 r45

                                                     Latest:
10.1. r53

---

### Post by lovinglinux on 2010-06-19
If you have a 64bit browser, then try this:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Add the following line before the last line of the file opened by the previous command:

```
export GDK_NATIVE_WINDOWS=1
```

Save and restart the browser.

---

