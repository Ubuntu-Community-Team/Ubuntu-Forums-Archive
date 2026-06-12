---
title: "update/install problem: dpkg status file"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by jangat on 2010-02-06
I recently tried to install updates.
The installation of updates was interrupted. Now, when I try to run update manager or synaptic, I get a message that says:

 dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
_cache->open() failed, please report.

When I run the command listed above, I get the following message:

dpkg: parse error, in file '/var/lib/dpkg/status' near line 489 package 'libelf1':
 file details field `Size' not allowed in status file

I would appreciate any help on how to correct this problem.

Thanks.

---

### Post by sisco311 on 2010-02-06
try switching to the backup list:
```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update

```

---

