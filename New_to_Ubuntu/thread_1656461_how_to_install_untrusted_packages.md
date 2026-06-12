---
title: "how to install untrusted packages"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by phyhanso on 2010-12-30
I am trying to install some applications using ubuntu software center but it is showing that the package is untrusted.Help me to how to install those kind of applications.

---

### Post by sgosnell on 2010-12-30
Just install them.  It's just a warning, not a fatal error.  Ignore the warning and install the packages.  Or you can add the key for the repository, if you want, and the warnings will go away,

---

### Post by phyhanso on 2010-12-30
Its not a warning after the dialog box opens I can't further install the application(there is just a OK option in the dialog box after it opens).Tell me how add the key for the repository.

---

### Post by sgosnell on 2010-12-31
If you have a problem with the software center, use Synaptic.  There are instructions for installing repository keys in the wiki and on numerous threads on the forums.  I no longer use Ubuntu, so I'm not certain how the software center works, but you should be able to go to the PPA, find a place to download the key, save it to your computer, then open the Software Sources tab in Edit Preferences, and click on Import Key File or something similar, then navigate to the key you downloaded.

---

### Post by Verbeck on 2010-12-31
try refreshing the package index files
close any software center/synaptic windows and run from a terminal (applications>accessories)
```

sudo apt-get update
```and try again

---

### Post by vacc73 on 2010-12-31
> **phyhanso said:**
> Its not a warning after the dialog box opens I can't further install the application(there is just a OK option in the dialog box after it opens).Tell me how add the key for the repository.
***You might also try downloading a program called ubuntu Tweak. It can be a helpfull shortcut to installing and managing software packages and ppa's***

---

### Post by cyb3r_sn4k3 on 2010-12-31
Did u try installing it from the terminal?

---

