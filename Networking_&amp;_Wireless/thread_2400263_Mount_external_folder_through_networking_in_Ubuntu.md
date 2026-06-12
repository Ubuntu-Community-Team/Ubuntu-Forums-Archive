---
title: "Mount external folder through networking in Ubuntu 18.04.1 LTS"
date: 2018-09-04
forum: Networking &amp; Wireless
---

### Post by sed_faster on 2018-09-04
Hello folks,

I have this system/environment:
```

 uname -a
Linux qw 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux $ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic

```

When I try run this command:
```

sudo mount -rt ip:/folder /media/path/client
mount.nfs: No such device

```

I did this:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nfs-common nfs-kernel-server
sudo apt-get install nfs-common

```

But the error keep. What do I do wrong?
This command still can be used in ubuntu 18.04.1 LTS?

Thanks

---

