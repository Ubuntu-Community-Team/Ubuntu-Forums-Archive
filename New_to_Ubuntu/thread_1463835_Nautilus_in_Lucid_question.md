---
title: "Nautilus in Lucid question"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by TalioGladius on 2010-04-27
In all previous versions, I could set nautilus to show the path of where I was as "/home/taliogladius/Desktop"  for example.  In lucid I can only get it to show the buttons.

Is there a way to set it permanently to the way I want it?

---

### Post by dv3500ea on 2010-04-27
You can press Ctrl-L to see the text box with the path in, but as far as I know, you can't set it to this permanently.

---

### Post by Shazaam on 2010-04-27
If all else fails you can try poking around in the Configuration Editor (if it's still there in Lucid)...
```
gconf-editor
```

---

### Post by antenna on 2010-04-27
yeah the gconf key is:

/apps/nautilus/preferences/always_use_location_entry

---

### Post by TalioGladius on 2010-04-27
> **antenna said:**
> yeah the gconf key is:

/apps/nautilus/preferences/always_use_location_entryWin.  


Thanks man

---

### Post by j_Antonio on 2010-10-27
Great! is working great! Make sure you are logged as super user. :guitar:

---

