---
title: "Firefox dies on 10.05 Upgrade"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by sdgreen on 2010-05-28
Just upgraded from U9.10 to U10.05. Firefox 3.6 worked for a period of 1 hour then died; will not start. Went to synaptic, removed all reference to firefox, restarted then reloaded firefox 3.6 from synaptic. Browser still would not start. Running U64bit on intel quad cpu box with 8gigs mem, and nvidia 8800GT vidcard. U 10.5 is updated as of 28May10.

Cannot figure out what is killing firefox! Where to look?

---

### Post by sandyd on 2010-05-28
> **sdgreen said:**
> Just upgraded from U9.10 to U10.05. Firefox 3.6 worked for a period of 1 hour then died; will not start. Went to synaptic, removed all reference to firefox, restarted then reloaded firefox 3.6 from synaptic. Browser still would not start. Running U64bit on intel quad cpu box with 8gigs mem, and nvidia 8800GT vidcard. U 10.5 is updated as of 28May10.

Cannot figure out what is killing firefox! Where to look?
what happens when you tun firefox from the terminal?
Open Applications -> Accessories -> Terminal and type in

```

firefox
```

---

### Post by lovinglinux on 2010-05-28
If you have libmoon installed, that could be killing Firefox. Remove it. Otherwise, see [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) an post here your results.

---

### Post by Ron S on 2010-05-28
When you removed fire fox did you remove the hidden .mozilla folder in your home directory. This can sometimes get corrupted in an upgrade.Firefox will create a new folder when restarted or reinstalled. You will lose your extension and bookmarks but it may fix the problem.You can also just rename the folder and if it fixes the problem copy extensions and bookmarks back into the new .mozilla folder one by one to see which if any of those was causing the problem.Good luck.

---

