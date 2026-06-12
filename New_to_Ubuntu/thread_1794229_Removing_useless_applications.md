---
title: "Removing useless applications"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by Linksku on 2011-06-30
Ubuntu 11.04 comes with 70+ apps, more than half of which I do not need. How can I remove them?

I tried removing LibreOffice using Software Center, but there are still many LibreOffice files and folders littered throughout my system. How can I thoroughly remove a software?

---

### Post by haqking on 2011-06-30
> **Linksku said:**
> Ubuntu 11.04 comes with 70+ apps, more than half of which I do not need. How can I remove them?

I tried removing LibreOffice using Software Center, but there are still many LibreOffice files and folders littered throughout my system. How can I thoroughly remove a software?


try using the synaptic package manager, when you check an app it usually marks all dependencies.

some programs have a uninstall.sh also.

---

### Post by dFlyer on 2011-06-30
My advice is to be very careful removing a lot of default applications. I've heard of people having libs problem when they removed many applications they felt were useless on a standard install. A command you can use from the command line to remove programs associated with the program you removed is:

sudo apt-get autoremove

Again be very careful.

---

### Post by Brushstroke on 2011-06-30
Try going into Synaptic and removing the packages through there. Make sure to check "Completely remove" and not just "Remove."

---

### Post by Cheesehead on 2011-06-30
Also, Software Center is set to rather benign defaults. For example, it won't remove systemwide config files, and it won't delete the compressed package copy sitting in your cache.
And no package manager will remove config files from your /home directory.

To really get rid of a package, you need to use Synaptic or (preferably) the command line.
```
sudo apt-get purge LibreOffice   # 'purge' removes system config files, too
sudo apt-get autoremove          # removes orphaned packages
sudo apt-get clean               # (OPTIONAL) delete your entire package cache
                            # Don't do it unless you understand the consequences!
```

---

