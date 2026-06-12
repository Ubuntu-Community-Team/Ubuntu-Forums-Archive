---
title: "Updates keep failing"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by cmcanulty on 2009-11-20
```
GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8F66051A3A258030Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch http://ppa.launchpad.net/amule-releases/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/chmsee/jaunty/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://wine.budgetdedicated.com/apt/dists/karmic/main/binary-i386/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.[CODE]
```[/CODE]

Can someone give some help on why I keep getting update error messages like the above? I am running Karmic. Now I always have an orange warning triangle on the top bar, thanks

---

### Post by KIAaze on 2009-11-20
It's because those repositories aren't available.

Edit your software sources (System->Administration->Software sources?). (Or synaptic->Edit repositories)
Remove the CD as source.
Then either remove the unavailable karmic repos or change them back to jaunty.

cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages.gz  
-> No Ubuntu CD in drive?

No karmic repos available yet:
fetch [http://ppa.launchpad.net/amule-releases/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/amule-releases/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
->[http://ppa.launchpad.net/amule-releases/ppa/ubuntu/dists/](http://ppa.launchpad.net/amule-releases/ppa/ubuntu/dists/)

Failed to fetch [http://ppa.launchpad.net/chmsee/jaunty/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/chmsee/jaunty/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
->[http://ppa.launchpad.net/chmsee/jaunty/ubuntu/dists/](http://ppa.launchpad.net/chmsee/jaunty/ubuntu/dists/)

Failed to fetch [http://wine.budgetdedicated.com/apt/dists/karmic/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
->[http://wine.budgetdedicated.com/apt/dists/](http://wine.budgetdedicated.com/apt/dists/)

---

### Post by bodhi.zazen on 2009-11-20
Nice one [KIAaze]("http://ubuntuforums.org/member.php?u=240158") , thank you for your detailed response =)

---

### Post by KIAaze on 2009-11-20
Thanks for the compliment. :)

There's still one unsolved line I think:
```
GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8F66051A3A258030

```

My guess would be a missing GPG key, but not sure which one.
They can also be added in the software sources dialog, altough this is a little bit more complex:
[https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab)

---

