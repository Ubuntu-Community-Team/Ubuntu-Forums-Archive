---
title: "How to reset apache2 back to default"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by hkl@hkl.no on 2008-12-04
Anyone

have been playing around with my apache, and would like it reset back to "default" to start all over with my setup.

do I need to remove or reinstall with an "overwrite" config option or ???

:confused:

Thanks in advance

hkl

---

### Post by dasunst3r on 2008-12-04
Perhaps you can go something like this:
```
sudo apt-get --purge remove apache2
```  The --purge option will delete configuration files again and uninstall Apache.  Then install again.

---

### Post by hkl@hkl.no on 2008-12-04
Sorry did not do the job, /etc/apache2/xxx was not touched by the un/reinstall.

Ended up reinstalling the server.

hkl

---

### Post by ki4jgt on 2011-11-09
anyone know how to do this yet?

---

### Post by mcduck on 2011-11-10
Yes. The "--purge" option for apt-get (or "Mark for complete removal" in Synaptic) should remove all system-wide configuration files for the package. Jsut make sure you actually remove the correct apache package.

...and in the end igf you have purged all apache packages and the config files still exist for some reason or other, just delete them yourself. That shouldn't happen, though, unless you actually forget to uninstall some apache package.

If you are messing with the settings, I would actually recommend making a backup of the original config files beforehands. Same goes for any config file, of course... :)

---

### Post by tsbartle on 2012-06-06
First, you need to completely remove all apache2 config files and directories

 **sudo apt-get remove --purge apache2 apache2-utils**

Then, reinstall apache2

 **sudo apt-get install apache2**

That worked for me, hope it does the trick for you too.

---

