---
title: "Problem with the  software center"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by gss2756 on 2011-08-26
I am new to ubuntu so please bear with me.When i open any specific category in the software center only the loading icon is displayed and it  doesnt  open even after a long time.
Please help. 


Thanks.

---

### Post by BlinkinCat on 2011-08-26
Yours is a new installation I assume? - 11.04 ?

---

### Post by HarrisonNapper on 2011-08-26
Are you able to get to Synaptic Package Manager in System>Administration? Also, try rebooting the computer and see if that helps.

---

### Post by gss2756 on 2011-08-26
Yes 11.04 
 i installed it just last week

---

### Post by HarrisonNapper on 2011-08-26
Also, if you haven't already run your updates, you can do so through System>Administration (or clicking the update icon in the top panel)

---

### Post by gss2756 on 2011-08-26
i cant open the package manager .Its showing error

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/
in.archive.ubuntu.com_ubuntu_dists_natty_main_binary-
i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by oldos2er on 2011-08-26
```
sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update
```

---

### Post by video editor on 2011-08-26
i suggest getting 10.04. 11.04 is new and almost experimental
i use it

---

### Post by gss2756 on 2011-08-27
@oldos2er
i tried the code but the package list could not be read:


Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


[]("http://ubuntuforums.org/member.php?u=338320")

---

### Post by gss2756 on 2011-08-27
@HarrisonNapper
i couldn't open the update  manager either:

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by oldos2er on 2011-08-27
> **gss2756 said:**
> @oldos2er
i tried the code but the package list could not be read:


Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


Could you post the output of **sudo rm /var/lib/apt/lists/* -vf** ?

---

### Post by gss2756 on 2011-08-27
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Index'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en%5fIN'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_Release'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_Release.gpg'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_i18n_Index'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en%5fIN'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_source_Sources'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_Release'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_Release.gpg'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Index'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en%5fIN'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_main_source_Sources'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_multiverse_i18n_Index'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_multiverse_i18n_Translation-en%5fIN'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_multiverse_source_Sources'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_Release'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_Release.gpg'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_restricted_i18n_Index'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_restricted_i18n_Translation-en%5fIN'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_restricted_source_Sources'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_universe_i18n_Index'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_universe_i18n_Translation-en%5fIN'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-i386_Packages'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty-updates_main_i18n_Index'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty-updates_main_i18n_Translation-en'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty-updates_main_i18n_Translation-en%5fIN'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty-updates_main_source_Sources'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_i18n_Index'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_i18n_Translation-en%5fIN'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_source_Sources'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty-updates_Release'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty-updates_Release.gpg'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_i18n_Index'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_i18n_Translation-en%5fIN'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_source_Sources'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_i18n_Index'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_i18n_Translation-en%5fIN'
removed `/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_source_Sources'
removed `/var/lib/apt/lists/lock'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/ppa.launchpad.net_sikon_steadyflow_ubuntu_dists_natty_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_sikon_steadyflow_ubuntu_dists_natty_main_source_Sources'
removed `/var/lib/apt/lists/ppa.launchpad.net_sikon_steadyflow_ubuntu_dists_natty_Release'
removed `/var/lib/apt/lists/ppa.launchpad.net_sikon_steadyflow_ubuntu_dists_natty_Release.gpg'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_i18n_Translation-en%5fIN'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_multiverse_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_multiverse_i18n_Translation-en%5fIN'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_multiverse_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_Release'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_Release.gpg'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_i18n_Translation-en%5fIN'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_universe_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_universe_i18n_Translation-en%5fIN'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_universe_source_Sources'

---

### Post by oldos2er on 2011-08-27
And now **sudo apt-get update** ?

---

### Post by gss2756 on 2011-09-22
sorry for replying this late but its working again thanks everybody for their help

---

### Post by technosysind on 2011-09-22
If your problem is solved then mark this thread as SOLVED ( thread tools )

---

