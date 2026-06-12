---
title: "update-manager error"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by jakuloy on 2011-05-14
Hi Every1,

Please help me with this....:(

'E:Encountered a section with no Package: header, 
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_multiverse_binary-i386_Packages, 
E:The package lists or status file could not be parsed or opened.'

I can't update and install new softwares because of this problem...:(

thanks in advance!!!!

---

### Post by Rubi1200 on 2011-05-14
Hi and welcome to the forums :-)

Open a terminal and run the following commands:
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

Let me know if this fixes the problem.

---

### Post by jakuloy on 2011-05-19
when update, it gives me this

---------------------------------------------------------------
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty-updates_main_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty-security_main_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
----------------------------------------------------------------

---

### Post by jakuloy on 2011-05-19
this is now my new problem:

'E:Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages (1),
E: Problem opening /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

