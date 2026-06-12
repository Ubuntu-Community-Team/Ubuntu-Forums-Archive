---
title: "No upgrade button on Update Manager Screen"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by smithwk2 on 2009-11-02
I am running Ubuntu 8.10 and I would like to upgrade to 9.10.  I understand that I have to upgrade to 9.04 first from 8.10.  I would like to do the network upgrade, but I do not have the New version line nor the upgrade button.  Any ideas on how to get that line and button to display?  Any help would be very much appreciated.

Wayne

---

### Post by slakkie on 2009-11-02
Hi, see the link in my signature (the fist one).

---

### Post by smithwk2 on 2009-11-02
Thanks for the help.  When I did the "sudo do-release-upgrade" it said "No new release found".  Any ideas?  Thanks.

Wayne

---

### Post by slakkie on 2009-11-02
Could you run *lsb_release -a* and *cat /etc/update-manager/release-upgrades* in a terminal?

---

### Post by smithwk2 on 2009-11-02
I changed the release-upgrades file from lts to normal and that worked.  Thanks for the help!!  I hope I can return the favor down the road....

Wayne

---

### Post by feydrutha on 2010-10-16
Same situation here on upgrade from 10.04 lucid to 10.10 maverick.

Changing "prompt=lts" to "prompt=normal" in /etc/update-manager/release-upgrades solved the problem.

---

### Post by smilodonis on 2010-10-16
[smithwk2]("http://ubuntuforums.org/member.php?u=472387") Please mark the thread as solved using the Thread tools on top right side.

---

