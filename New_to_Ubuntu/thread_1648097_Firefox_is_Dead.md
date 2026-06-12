---
title: "Firefox is Dead"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by hmsiegel on 2010-12-18
First I have to say that I have been using Ubuntu for a week now and have yet to boot into Windows.  Granted, my computer at work is Windows, which is where I spend a lot of time, but still....
I have an issue now.  Firefox won't open.  I don't know what I did, but if I go to open it, it just brings up the Firefox Crash report and then closes.  Nothing.  I don't really use Firefox all that much (I like Chrome), but it's nice to have options, especially when pages aren't loading properly.

Thanks

Harlan

---

### Post by davidmohammed on 2010-12-18
open a terminal session and then type firefox

if there are any errors reported, copy and paste the errors into a reply here.

---

### Post by susema on 2010-12-18
Try this in terminal;

```
rm -rf .mozilla
```

---

### Post by cameronedwards on 2010-12-18
Try to uninstall and then reinstall through Ubuntu Softer Centre.

---

### Post by hmsiegel on 2010-12-18
> **susema said:**
> Try this in terminal;

```
rm -rf .mozilla
```

That worked.  What did it do?  I know that rm is remove, and that the -rf recursively forces, but the .mozilla I'm not sure about.  

Thanks though

Harlan

---

### Post by davidmohammed on 2010-12-18
.mozilla holds all the configuration files that firefox uses.  If you delete and then start firefox, it gets recreated with a bunch of default values

You normally cant see the folder since it is "hidden"  - all folders beginning with "." are similarly hidden from normal view in nautilus file manager

---

### Post by lotharmat on 2010-12-18
Always the best way to solve FF problems - Nuke the profile!

---

### Post by themusicalduck on 2010-12-18
For the record though for anyone else reading this, I'm fairly sure deleting the .mozilla folder also deletes all bookmarks and other things to do with your profile!

---

### Post by lovinglinux on 2010-12-19
> **susema said:**
> Try this in terminal;

```
rm -rf .mozilla
```

Please don't recommend that. Using "rm -fr" is an unrecoverable command that will completely wipe the user's Firefox profile. While deleting the profile indeed solves most of the problems in Firefox, recommending that command, specially without even alerting the user that he will loose all bookmarks, passwords and personal settings forever, is kind of irresponsible.

Don't get me wrong, is just that I for one would really mad if I follow a recommendation from the forum and then lose important stuff like Firefox bookmarks and passwords.

There are other ways of [fixing a corrupted profile]("http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html"). Use deletion as last resort.

---

