---
title: "Firefox runs for a minute, then shuts down."
date: 2009-02-21
forum: New to Ubuntu
---

### Post by beswatcher on 2009-02-21
Ubuntu 8.04 26.24-23
Firefox was running well until boot today. On start up Firefox goes whereever I send it, but only runs for a minute, and completely shuts itself down. I have re-booted 3 times and get the same result, so I'm using Konqueror at the moment.

When I try to open Package manager, add/remove programs, or Synaptic I get the same result. Any help I can get will be appreciated.

---

### Post by Cresho on 2009-02-21
backup your bookmarks and passwords if you want and then close all instances of firefox.  open up places->home.  In file browser application, hit view->"show hidden files" then look for .mozilla and delete it. 

now start up firefox and your done.  restore your bookmarks and passwords if you want.

---

### Post by beswatcher on 2009-02-21
> **Cresho said:**
> backup your bookmarks and passwords if you want and then close all instances of firefox.  open up places->home.  In file browser application, hit view->"show hidden files" then look for .mozilla and delete it. 

now start up firefox and your done.  restore your bookmarks and passwords if you want.

Thanks ! Firefox seems to work fine now after your cure.

Now if I could get Synaptic Package manager and the updates to not fizzle out after 15 seconds, I'd be OK. Any ideas for these? Even after a re-boot I am told "A problem occurred while checking for updates".

I seem to have found the answer [http://ubuntuforums.org/showthread.php?p=6774846#post6774846]]("http://ubuntuforums.org/showthread.php?p=6774846#post6774846")

Tomorrow I'll bother everyone about not being able to stream radio stations who are online. Thanks again!

---

### Post by Cresho on 2009-02-21
open up terminal

```
sudo apt-get update
sudo apt-get upgrade
```

you may need to add an -f to repair or attemt to repair broken dependencies.

---

### Post by tomthumb99 on 2009-03-01
For those new to Ubuntu, these two commands are the most dangers at times.  You never know what you are going to get, its like an old sikzo girlfriend of mine (ie: some times good, somes time bad). 

sudo apt-get update
sudo apt-get upgrade

Said another way, you can blow up you whole system at times with these bulk upgrades.  For me it take two days to repair some of the damage.  I found it is much much safer to use the synaptic packagae manager and be selective in choosing upgrades.... (Yes, its tempting to think that upper right red arrow is going to solve all of your problems, it does not) 

NOTE: Why upgrade packages that you never use, if OpenOffice works for you, don't touch it.

---

