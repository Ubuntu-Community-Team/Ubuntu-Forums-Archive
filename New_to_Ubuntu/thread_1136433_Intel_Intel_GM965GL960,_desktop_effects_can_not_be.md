---
title: "Intel Intel GM965/GL960, desktop effects can not be enabled"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by laffinet on 2009-04-25
Hi !

I've just done a fresh install of 9.04 and can't enable desktop effects anymore. When I try I get the message "Desktop effects can not be enabled".

This is the relevant lspci

```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
```

This is what I get when from compiz:
```

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 

```

There are no restricted drivers on the systems.

Any help is much appreciated.

---

### Post by Dynaflow on 2009-04-25
Do this:  [http://ubuntuforums.org/showpost.php?p=7132843&postcount=5](http://ubuntuforums.org/showpost.php?p=7132843&postcount=5)

---

### Post by laffinet on 2009-04-25
Thanks. Worked like a charm.

---

### Post by sundar_ima on 2009-04-25
Thank you man. It works perfectly for me...

---

### Post by pjones0404 on 2009-04-25
this worked for me as well. 

It will pretty easy to undo as well if the fix the bug that caused them to blacklist the intel drivers. 

thanks a lot!

---

### Post by sinbin on 2009-04-25
Worked for me as well. Sweet

---

### Post by blackened on 2009-04-25
A much easier way is to add the skip check line to ~/config... as suggest at the bottom of this page -> [http://wiki.compiz-fusion.org/Hardware/Blacklist]("http://wiki.compiz-fusion.org/Hardware/Blacklist").

---

### Post by laffinet on 2009-04-25
While this did work for me as said earlier, I know have a different problem:

I can't install compizconfig-settings-manager

When I try to I get an error message saying that there are unresolved dependencies. Any ideas ?

---

### Post by blackened on 2009-04-25
> **laffinet said:**
> While this did work for me as said earlier, I know have a different problem:

I can't install compizconfig-settings-manager

When I try to I get an error message saying that there are unresolved dependencies. Any ideas ?

This should probably be started as a new thread.

What dependencies does it name as unresolvable?

---

