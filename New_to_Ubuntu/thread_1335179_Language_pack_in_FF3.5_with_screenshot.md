---
title: "Language pack in FF3.5 with screenshot"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by Marti68 on 2009-11-23
Hi All,

Inadvertantly installed a language pack into FF3.5 browser.  The package works but no obvious way of getting back to english.  Upgraded from 9.04 to 9.10 all with out success.  Removed and reinstalled every FF option via Software Centre and Synaptic Manager (do they do the same thing?).  Still there.  About ready to format and start again but hope you've got a better idea as a duel boot will take time to rebuild.

Screen-shot attached.
Thank for your advice on this.  Clonezilla image before any and every change next time

---

### Post by wojox on 2009-11-23
Go to places > home folder and press Ctrl+H and look for .mozilla as that is where your config files are.

---

### Post by ukripper on 2009-11-23
Go to System-->Administration-->Language Support it will install new language for you if english is not already there.

---

### Post by Marti68 on 2009-11-23
Thank you for trying guys :)

Language support set to English for both, as expected.  Everything else is fine.  Deleted FF3.5 again AND manually deleted the Mozilla directories you directed me to.  Rebooted, reinstalled and showing FF menus incorrectly; ie the unrecognised script.

Repeated but installed via Synaptic as well as Software Centre with the same result

---

### Post by ukripper on 2009-11-23
in firefox address bar type:
```
about:config
```

then in filter field type language and see if it is set to english (en)?

---

### Post by Marti68 on 2009-11-23
Thanks UKRipper,

Followed that and matched the string to the desktop (which is fine) en-gb, en.  (the "I'll be careful" warning is a nice human touch) Also, matched the userset to langpack-gb etc.

Alas, no luck
EDIT, should have mentioned that the userset WAS set to x-Cryllic

---

### Post by ukripper on 2009-11-23
can you do the same about:config and in filter this time put this ```
general.useragent.locale
```

double click on it and change it to en-GB if set to something else

---

### Post by Marti68 on 2009-11-23
> **ukripper said:**
> can you do the same about:config and in filter this time put this ```
general.useragent.locale
```double click on it and change it to en-GB if set to something else

Set as you suggested but no luck unfortunately.  Decided to format and rebuild the duel boot from scratch.  Thanks for all your suggestions.  Next time I'll image before touching anything.

---

