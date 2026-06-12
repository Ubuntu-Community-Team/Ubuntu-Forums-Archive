---
title: "My shutdown scripts aren't running (rc0.d/rc6.d, etc)"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by ronaldrand on 2009-03-10
My shutdown seems to be broken. For example, no scripts I install that are supposed to run at logout/shutdown/restart actually run. Also, every time I start Firefox it tells me it previously crashed and do I want to restore the session. I don't think my shutdown is happening properly. It happens really fast. Anybody have any ideas? This is on an Intrepid install.

---

### Post by skymera on 2009-03-10
```
 sudo apt-get install sysv-rc-conf 
```

Adjust the runlevels using that :)

---

### Post by ronaldrand on 2009-03-10
> **skymera said:**
> ```
 sudo apt-get install sysv-rc-conf 
```Adjust the runlevels using that :)

Thanks, that seemed to fix my problem with my scripts. However, I'm still having an issue with Firefox saying it crashed every time I reboot. I guess that's just a hindrance I'll have to live with.

---

### Post by mikechant on 2009-03-10
> However, I'm still having an issue with Firefox saying it crashed every time I reboot. I guess that's just a hindrance I'll have to live with.

Have you tried deleting your Firefox profile in case it's corrupt(probably after exporting your bookmarks so you can reimport them)?
See [http://support.mozilla.com/en-US/kb/Profiles](http://support.mozilla.com/en-US/kb/Profiles) and click on "Show content customized for: Linux".

---

### Post by ronaldrand on 2009-03-10
> **mikechant said:**
> Have you tried deleting your Firefox profile in case it's corrupt(probably after exporting your bookmarks so you can reimport them)?
See [http://support.mozilla.com/en-US/kb/Profiles](http://support.mozilla.com/en-US/kb/Profiles) and click on "Show content customized for: Linux".

I just tried it. I backed up my bookmarks, deleted the Profile folder and the profiles.ini file as per the page you sent me to. I rebooted. No luck! Same error message and annoying prompt.

---

