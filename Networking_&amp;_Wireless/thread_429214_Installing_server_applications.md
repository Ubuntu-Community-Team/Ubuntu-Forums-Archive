---
title: "Installing server applications"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by Uranium235 on 2007-05-01
Is it possible to install the server applications such as Apache into regular Ubuntu?  Thus far the download mirrors have given me corrupted iso's 3 times tonight (could be the burn, but I burnt it at 4x to avoid that problem.)

---

### Post by amohanty on 2007-05-01
Yup.

sudo apt-get install apache2

HTH
AM

---

### Post by Uranium235 on 2007-05-01
So what are the commands to get the other core Ubuntu server software packages?

---

### Post by amohanty on 2007-05-01
Typically enabled universe repositories:
[https://help.ubuntu.com/community/Repositories#head-9067080b61c44973ed11e270ba73fe4ec8ed05a0](https://help.ubuntu.com/community/Repositories#head-9067080b61c44973ed11e270ba73fe4ec8ed05a0)

and then use
System->Administration->Synaptic to find and install software

OR if you know the names of the software, just use apt-get install ....

Its the analogue or yum (redhat/suse) or emerge(gentoo) or bsd ports (sort of)

HTH
AM

---

