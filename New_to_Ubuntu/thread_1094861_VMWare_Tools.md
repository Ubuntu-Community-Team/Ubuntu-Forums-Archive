---
title: "VMWare Tools"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by Cheesemill on 2009-03-13
First you need to install the packages required to build the tools:

```
sudo aptitude -y install build-essential linux-headers-$(uname -r) psmisc
```

Using VMware Web Access mount the VMware Tools CD by selecting the machine and clicking Install VMware Tools.

The following commands will build the tools and then clean up the working directory :

```
mount /media/cdrom
cd /tmp
tar -xvzf /media/cdrom0/VMwareTools*.gz
sudo vmware-tools-distrib/vmware-install.pl -d
rm -rf vmware-tools-distrib
```

Hope this helps,
Cheesemill.

---

