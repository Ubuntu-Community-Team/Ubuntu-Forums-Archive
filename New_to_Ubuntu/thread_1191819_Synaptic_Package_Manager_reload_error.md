---
title: "Synaptic Package Manager reload error"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by Ghundio on 2009-06-19
Hi, I'm pretty new to ubuntu and was hoping for some help regarding the Synaptic Package Manager. 
When I press the reload button in the Synaptic window it begins to update and then I receive this error message:

> 
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg](http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-en_US.bz2)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/jaunty/Release.gpg](http://wine.budgetdedicated.com/apt/dists/jaunty/Release.gpg)  Could not resolve 'wine.budgetdedicated.com'

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/jaunty/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not resolve 'wine.budgetdedicated.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
I currently have the following software sources:
[IMG]http://img523.imageshack.us/img523/2708/softwaresourcespic.jpg[/IMG]

Any help would be greatly appreciated.

---

### Post by Therion on 2009-06-19
Just a connection error, it'll resolve itself.  In the meantime just use a different server.

See pic: 

[IMG]http://web2.justhost.com/~buranen1/wp-content/uploads/2007/10/screenshot-software-sources1.png[/IMG]

Use the menu for "Download from" and just choose a different server. Reload and run the update manager again.

---

### Post by Ghundio on 2009-06-19
Thank you, that fixed the problem perfectly.

---

