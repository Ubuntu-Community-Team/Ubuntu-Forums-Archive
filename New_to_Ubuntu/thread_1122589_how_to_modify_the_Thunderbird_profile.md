---
title: "how to modify the Thunderbird profile"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by Jack Shankle on 2009-04-11
I need to modify my Thunderbird profile in Ubuntu but can't find the profile
to do it. My knowledge of Ubuntu is sparse.
Thank you,

---

### Post by philinux on 2009-04-11
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

Places > Home folder then press ctrl h to show hidden folders and files.

---

### Post by 73ckn797 on 2009-04-11
Once hidden files and folders are enabled look for ".mozilla thunderbird".

---

### Post by presence1960 on 2009-04-11
> **Jack Shankle said:**
> I need to modify my Thunderbird profile in Ubuntu but can't find the profile
to do it. My knowledge of Ubuntu is sparse.
Thank you,

To open profilemanager for Thunderbird open a terminal(Applications>Accessories>Terminal) and enter ```
thunderbird -profilemanager
```

your thunderbird files are located at /home/.mozilla-thunderbird

That is a hidden folder in the home directory. Open file browser & in home press Ctrl+H to show hidden files and directories. Hope this helps.

---

