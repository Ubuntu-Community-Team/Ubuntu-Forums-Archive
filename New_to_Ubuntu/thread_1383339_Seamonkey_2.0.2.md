---
title: "Seamonkey 2.0.2"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by bobanshirl on 2010-01-17
I have installed Seamonkey which is ver 1.1.17.When I run it,it tells me to download the later version 2.0.2.I have got Seamonkey 2.0.2.tar.bz2 on my desktop.I need to know a,How do I install it,b,do I have to uninstall ver 1.1.17 before installing 2.0.2,and if so how do I uninstall. Thanks in anticipation.

---

### Post by VCoolio on 2010-01-17
You can extract the archive where you want and run seamonkey from in there. No need to install. User configs will be stored in ~/.mozilla/seamonkey

---

### Post by mkvnmtr on 2010-01-17
I replaced the old Seamonkey by using the Ubuntuzilla repository. Go to their page and it will explain how to add their repository. I removed the old Seamonkey first with Synaptic and then enabled the repository. I downloaded Seamonkey 2.03. Then I disabled the repository in software sources because I did not want their Firefox or Thunderbird. When I see there is an update I will reenable the repository , get it and then disable again.

---

### Post by nanotube on 2010-01-17
> **mkvnmtr said:**
> I replaced the old Seamonkey by using the Ubuntuzilla repository. Go to their page and it will explain how to add their repository. I removed the old Seamonkey first with Synaptic and then enabled the repository. I downloaded Seamonkey 2.03. Then I disabled the repository in software sources because I did not want their Firefox or Thunderbird. When I see there is an update I will reenable the repository , get it and then disable again.

there's no need to disable the repository if you don't want firefox or thunderbird (or seamonkey, for that matter). the packages in the ubuntuzilla repository are named <package>-mozilla-build, so if you don't install the packages, you'll not be bothered about installing them. they do /not/ overwrite the ubuntu-repositories packages (like the mozilla-daily repository does), so this is not a problem.

you're kind of defeating the whole purpose of using the repository (automatic updating) by disabling it, and manually checking for updates. 

that said, for the original poster, here's the project site for ubuntuzilla:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

