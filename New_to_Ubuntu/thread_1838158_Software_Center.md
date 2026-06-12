---
title: "Software Center"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by prakharmohan on 2011-09-03
I started using Ubuntu 11.04, the problem is that the software center is not working, that is, its not showing the apps and the programs. Secondly Synaptic Package Manager is not working. What to do??:confused:

---

### Post by BlinkinCat on 2011-09-03
Have they worked in the past?

---

### Post by saltmarshlamb on 2011-09-03
What errors do you get if you try and open synaptic through a terminal - 

```
gksudo synaptic
```

Try running this through a terminal - paste the output

```
sudo apt-get update
```

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)


You need to be more specific when stating your issue - no-one can guess what you mean :)

[http://ubuntuforums.org/showpost.php?p=8920811&postcount=1](http://ubuntuforums.org/showpost.php?p=8920811&postcount=1)

---

### Post by scruffyeagle on 2011-09-03
I've only worked w/ v10.04 LTS, but I suspect that this advice could still be useful for you.

It would be good to verify that the User profile you're trying to perform these operations from is listed in the "sudo" group. If your current profile doesn't have Admin privileges, then switch to one that does. (That alone will probably solve the problem; i.e., you can probably download w/o problem from an Admin profile.) In the Admin profile, open the "Users and Groups" dialogue off the system/Administration menu. Click on the "Groups" button, then scroll down the list of groups. Find the group title "sudo". Edit the properties to find if the User profile you've been having troubles in is checkmarked. If not, then checkmark it and exit. Log out of Admin and log into that User. See if you can now go for software.

---

