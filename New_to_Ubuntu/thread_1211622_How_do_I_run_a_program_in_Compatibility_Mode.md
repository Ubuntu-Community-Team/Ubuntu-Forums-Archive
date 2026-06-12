---
title: "How do I run a program in Compatibility Mode?"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by bmtlol on 2009-07-12
I specifically want to run a program in compatibility mode for Windows 95 or 98, though the option is not in properties if I right-click the icon.

---

### Post by nhasian on 2009-07-12
are you trying to run windows programs in linux?  you'll need wine to do that.

```
sudo apt-get install wine
```

---

### Post by Rocket2DMn on 2009-07-12
When you have Wine installed, you can go to Applications->Wine->Configure Wine, where you can set what mode to run programs in.  You should also be able to specify which mode to use for specific programs, though I haven't personally tried myself.
Alternatively, you can access the configuration utility from terminal:
```
winecfg
```

What program are you trying to run?

---

### Post by Bradtek on 2009-07-12
Click on Link in My Sig

---

