---
title: "no automatic install of linux headers and modules upon upgrade"
date: 2021-04-01
forum: Networking &amp; Wireless
---

### Post by dieter-erich on 2021-04-01
Hi,
   some time ago I screwed my ubuntu-20.04 probably by inadequate use of Ubuntu Cleaner. jermey31 was extremely helpful and with his aid I managed to install the lacking headers and modules. 
However, this does not automatically occur upon upgrade. So, I must always run through the following procedure:

ls -l /usr/src/linux-headers-$(uname -r)
sudo apt install linux-headers-$(uname -r)
sudo apt install --reinstall linux-headers-$(uname -r)-generic linux-modules-extra-$(uname -r)-generic

what do I need to do to have it automatically installed as is normally the case on upgrade?

Thanks, D.E.

---

### Post by deadflowr on 2021-04-01
You need the generic headers meta-packages.
But better to just have the linux-generic package installed.
That package will install the linux-image-generic and linux-headers-generic packages.
Which in turn will install the latest versions for both whenever updates comes for them.
```
sudo apt install linux-generic
```

If using the [hwe stacks]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") it might be either
```
sudo apt install linux-generic-hwe-18.04
```
For Ubuntu 18.04
or
```
sudo apt install linux-generic-hwe-20.04
```
for Ubuntu 20.04.

(The linux-modules-extras are a dependency of the linux-image-generic meta-package so ti should e updated as well.)

---

### Post by dieter-erich on 2021-04-01
Thanks a lot! I installed it and shall see when running the next upgrade. Things often seem very easy - provided one knows :-)

---

