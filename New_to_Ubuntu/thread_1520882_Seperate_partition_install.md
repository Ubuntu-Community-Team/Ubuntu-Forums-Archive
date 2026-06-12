---
title: "Seperate partition install"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by telltom on 2010-06-30
When i installed Ubuntu, i gave / and home and swap its own partition in the event i change distros i can keep my info. How to i reinstall and not over write home? Or if i upgrade how will the upgrade not overwrite?

---

### Post by mikewhatever on 2010-06-30
Upgrades don't overwrite personal files, that's why they are upgrades. ;)
If you reinstall from cd, go with the manual partitioning and assign each its appropriate mount point. Make sure you don't click the format box for /home.

---

### Post by indytim on 2010-06-30
If you have the real estate for new partitions, when you install new distro's or revisions, do it to fresh partitions.  Post install, just drag your critical configuration files/folders from your production distro to the new app's /home.

In a lot of the distro's they are offering a migration assistant that will ask you during the installation if you want to import your settings from an existing install.  That makes it easier than what I have outlined above (if available).

Again, this all applies to installing on different partitions from your production partition.  Installing over the existing does not apply.

Hope this additional information helps.

IndyTim / DataMan

---

