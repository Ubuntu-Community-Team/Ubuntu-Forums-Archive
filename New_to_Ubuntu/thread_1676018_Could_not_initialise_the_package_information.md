---
title: "Could not initialise the package information"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by yonthan on 2011-01-26
Hey guys :)

I Recently got this error when Ubuntu was updating. Now it wont update.

There error reads:

Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Any help would be much appreciated :)

---

### Post by Wobblybob on 2011-01-26
If this was me I'd navigate to the folder /var/lib/apt/lists then delete the file called security.ubuntu.com_ubuntu_dists_maverick-security_main_binary-i386_Packages which is mentioned in the error message then try running.

sudo apt-get update again, if no errors Bob's your Uncle :P

---

