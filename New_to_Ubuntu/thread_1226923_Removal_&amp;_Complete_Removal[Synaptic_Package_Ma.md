---
title: "Removal &amp; Complete Removal[Synaptic Package Manager]"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by Hoom@n on 2009-07-30
What's the difference between "Removal" & "Complete Removal" in Synaptic Package Manager?

---

### Post by MelDJ on 2009-07-30
removal removes only the selected package while complete removal removes the package and its dependencies i think

---

### Post by Hoom@n on 2009-07-30
> **MelDJ said:**
> removal removes only the selected package while complete removal removes the package and its dependencies i think
You are right(I tested it before); but, will they remove downloaded packages from computer hard disk?
+(I prefer to always have an copy of the downloaded files and never download one file twice)

---

### Post by sarfarazkazi on 2009-07-30
I guess complete removal removes any configuration files related to the application.

---

### Post by HotShotDJ on 2009-07-30
Removal = remove the selected package
Complete Removal = remove the selected package along with configuration files.

After you do a complete removal, you might want to run the following commands from a terminal to get any cruft left behind:
```
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean
```"autoclean" will get dependency that "complete removal" might miss.  You don't need to run both "clean" and "autoclean" -- choose one based on your wishes:[QUOTE="http://www.debian.org/doc/manuals/apt-howto"]apt-get clean removes everything except lock files from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. Thus, if you need to reinstall a package APT should retrieve it again.

apt-get autoclean removes only package files that can no longer be downloaded.[/QUOTE]
You might also want to read "[How to Spring-Clean an Apt-based Distribution]("http://www.freesoftwaremagazine.com/columns/how_to_spring_clean_an_apt_based_distro")."

---

### Post by Hoom@n on 2009-07-30
> **HotShotDJ said:**
> Removal = remove the selected package
Complete Removal = remove the selected package along with configuration files.

After you do a complete removal, you might want to run the following commands from a terminal to get any cruft left behind:
```
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean
```"autoclean" will get dependency that "complete removal" might miss.  You don't need to run both "clean" and "autoclean" -- choose one based on your wishes:
You might also want to read "[How to Spring-Clean an Apt-based Distribution]("http://www.freesoftwaremagazine.com/columns/how_to_spring_clean_an_apt_based_distro")."
So, "remove" won't delete packages from hard disk and "clean" deletes from hard disk; am I right?

---

### Post by HappyFeet on 2009-07-30
> **Hoom@n said:**
> So, "remove" won't delete packages from hard disk and "clean" deletes from hard disk; am I right?

Yes.

---

### Post by magmon on 2009-07-30
Removal takes out the package, complete removal removes the package and all traces related to it. I recommend you always click complete and see what it will remove, if you need any of it, select regular removal. If you dont, go ahead with the complete.

---

### Post by Hoom@n on 2009-07-31
Thanks!

---

