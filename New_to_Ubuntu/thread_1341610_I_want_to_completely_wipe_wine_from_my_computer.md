---
title: "I want to completely wipe wine from my computer"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by chris tallman on 2009-11-29
I installed wine and tried installing iTunes on it and that was a massive failure. Now I am unable to get rid of it or its leach Quicktime. I decided to delete the beta version of 1.1.33 to install the stable one but the stable one wont install, it keeps saying'
> This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.I went into my home folder and deleted the .wine folder but the program folders still remain in the applications drop down with no version of wine installed. I have also tried
> sudo apt-get remove --purge wine and it doesn't seem to make a difference. Can anyone help me make it seem like wine was never here. I'm on Ubuntu 9.10. Thanks!

---

### Post by ed-koala on 2009-11-29
It should be as simple as going in Synaptic Package Manager, finding wine, choosing mark for complete removal ... also do that for wine geko and playonlinux ...

Once that's done, you can check your home folder and delete your .wine directory ...

Then, go to System - Preferences - Main Menu and edit that to remove all your wine entries, then everything should be gone.

Am I missing anything gurus?

---

### Post by bumanie on 2009-11-29
Follow this [guide]("http://wiki.winehq.org/FAQ#head-9893ae50079ca7a959258f0bc9a17aaf2e69b391") from the winehq site.

---

### Post by chris tallman on 2009-11-29
There is no mark for complete removal, and my .wine folder is gone but I can still reinstall the beta version of wine, just not the stable one.

---

### Post by chris tallman on 2009-11-29
Ok so the guide on their site removed everything, but I still get the same error message when I try to install the stable version?
> This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.

---

### Post by bumanie on 2009-11-30
You could try to install wine from source, rather than using the .deb version.

---

