---
title: "&quot;Could not download all repository indexes&quot; preventing me from upgrading!"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by RayleenCourtney on 2010-06-30
I am trying to upgrade my laptop from Ubuntu 8.04 to 10.04. When I check for updates in the Update Manager to begin this process, I get this message:

[I]Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.[/I]

Followed by:

[I]Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.[/I]


I have looked through the forums on here and tried to solve this problem via update commands in the terminal (I had a similar problem on my desktop computer before upgrading it and fixed it just fine), but something just isn't working. I believe I am correct in that when these updates are successfully installed, my Update Manager will give me the option to upgrade to 10.04, yes?

Thanks ahead of time for your help, Ubuntu Awesome Ones!

---

### Post by drs305 on 2010-06-30
Open Synaptic or Software Sources. Go to Settings, Repositories and untick the entry for your install CD in the lower panel. You may have additional CD references in one of the other tabs, such as "Other Software" or "Third Party Software". After unticking the CD references, press "Reload" from the top menu.

What is happening is that Synaptic is searching for the CD from which you installed Ubuntu. Since it can't find it, it tells you so.

---

### Post by RayleenCourtney on 2010-06-30
Once again, the Ubuntu Forums save me! Thanks, DRS! I'll mark this thread as solved.

One last question though-- it still isn't giving me the option to upgrade to 10.04 after I re-check for updates. Am I incorrect in thinking the upgrade is possible via Update Manager?

---

### Post by drs305 on 2010-06-30
I don't have my Hardy VM available at the moment, but you might check Update Manager's Updates tab (or equivalent) and see if the 'Release Upgrades' option is enabled.

Otherwise, here is a good reference for updating releases:
[https://help.ubuntu.com/community/LucidUpgrades]("https://help.ubuntu.com/community/LucidUpgrades")

Note: Running the upgrade from the command line may show any potential problems which may be preventing you from updating with Update Manager.

---

### Post by RayleenCourtney on 2010-07-01
Thank you so much!!!

---

