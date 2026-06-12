---
title: "Battery Power Indicator"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by iamsd on 2010-09-27
Hi all

I accidentally removed the battery power indicator on the upper panel of my Ubuntu Lucid. I tried adding back the widget, but couldn't find it the list.

Any pointers?

Thanks

---

### Post by andrewthomas on 2010-09-27
```
rm -r ~/.gconf/apps/panel
```To restore panel to default.
Then log-out and back in.

---

