---
title: "Upgrade/partitioning"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by Messyhair42 on 2009-10-03
I'm currently using Jaunty on a 1 TB drive, I've got /,/swap./usr,/var,/temp, and /home on separate partitons, with /usr being the only partition being close to full (70% of 4 GB). if i were to upgrade to karmic when it comes out what would I lose? I'm concerned about the programs i have installed (Wine, Compiz, Prime 95, VLC, Songbird, Ktorrent, java/flash/other plugins) that aren't necessarily simple to configure. i know programs *SHOULD* be within /usr, and i it doesn't get erased with an upgrade, but how to i check the location of these programs? and would it be safe to upgrade without undoing all my hard work in setting up my system?

---

### Post by Paqman on 2009-10-03
When you upgrade, the system replaces your packages from the Kaunty repos with new ones from the Karmic repos. Nothing is wiped, as such. It's just like performing a really big version of the normal updates you get.

If you're using PPAs or 3rd party repos, it's safest to disable them during the upgrade. You can re-enable them after, but it's possible that any apps you installed from them may be broken in the transition to the new system.

A major upgrade like this would be a good opportunity to make sure your backups are up to date, just in case.

---

