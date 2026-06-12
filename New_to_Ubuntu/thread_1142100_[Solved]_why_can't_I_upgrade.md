---
title: "[Solved] why can't I upgrade?"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by 4me on 2009-04-28
I have used Ubuntu for at least a year and a half (2-3 upgrades) and used the update manager.   it is not in my update manager yet(should it be?).....is there another way for me to do it?

---

### Post by tricolorpoa on 2009-04-28
try this
```
# sudo update-manager -d
```

---

### Post by angelsneverdie on 2009-04-28
Look in the system menu, administration, software sources.  I found that the last version had set the option in the updates tab to show long term releases only.  try changing that to "normal releases".

if that is already set correctly, it could be that your computer wants to check the hard drives.  if you've been pressing escape to bypass this procedure when you boot up, you'll need to let it run before it will let you upgrade.

---

### Post by 4me on 2009-04-28
changed to 'normal releases'....and got it.   thanks.

---

### Post by angelsneverdie on 2009-04-29
No problem, I am glad you got it working!

---

