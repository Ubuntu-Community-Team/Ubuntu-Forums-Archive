---
title: "Failed to download repository information"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by quomodo on 2011-05-15
New to Ubuntu. I updated to 11.04 from 10.10. It was running great at first, however, I had installed some packages and must have done something wrong. Now I get this error if I try to run Update Manager:

```
Failed to download repository information
Check your Internet connection.

W:Failed to fetch http://ppa.launchpad.net/ubuntu/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/ubuntu/ppa/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

All help is appreciated, thanks.

---

### Post by Rocket2DMn on 2011-05-15
Not sure what the PPA is for, but you can disable by clicking the session indicator in the upper right bar of the Unity interface, and going to System Settings.  Choose Software Sources, then uncheck the PPA from Other Software.  When you close the window it will ask you to reload your sources, so click Reload.  Now when you run Update Manager, it should go smoothly.

---

### Post by quomodo on 2011-05-15
Fixed it, thank you. Any idea where that source came from?

Also, how can I get my software sources back to "factory settings"? I have a feeling I screwed around in there a bit too much while trying to fix this error and I may have added or got rid of something important..

---

### Post by Rocket2DMn on 2011-05-15
I'm not sure where that source came from, it looks like a PPA mirror of the main repository, which doesn't make any sense to me.

If you want more or less default settings, you should have the first four boxes checked under the Ubuntu Software tab (main, universe, restricted, multiverse) - I'm not sure if universe is enabled by default these days, but multiverse probably is not. Under the Updates tab, you will want the first two checked (natty-security and natty-updates).  I wouldn't check the other two unless you know what you're doing.

The Other Software tab has misc repos that are usually not default, though in Natty I'm seeing "Independent" which looks like an Ubuntu supported repository, so it's probably safe to leave it checked.

---

### Post by wildmanne39 on 2011-05-15
> **quomodo said:**
> Fixed it, thank you. Any idea where that source came from?

Also, how can I get my software sources back to "factory settings"? I have a feeling I screwed around in there a bit too much while trying to fix this error and I may have added or got rid of something important..
Hi, I had that ppa also not sure why but I just unchecked it, it showed up after an upgrade.

---

### Post by offbeat404 on 2011-08-12
i had the same issue. removed the cd-rom option from software resources (synaptic manager) and seems to be working like a charm now.

ps: it might have been a late response but i just figured it out :)

---

### Post by Lankster on 2011-11-17
Just got this one? any help??

Failed to download repository information:


W:Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by alizzi on 2012-11-26
Thanks.

---

### Post by wildmanne39 on 2012-11-26
Old thread closed.

---

