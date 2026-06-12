---
title: "rename samba domain controller"
date: 2019-08-19
forum: Networking &amp; Wireless
---

### Post by james-sonifex on 2019-08-19
I have an active directory domain with 2 domain controllers one that acts as the primary and another that acts as afileserver as well as a backup domain controller.

I've created a replacement file server using zentyal and a few manual tweaks but have had to give a different netbios name whilst testing and copying files from the existing DC. My question is if and when I'm happy with it how can I change it's name to be what the current fileserver is?

I've tried simply changing the netbios name in samba.conf this changes its name on the netwrok but doe snot modify its active directory configuration as a domain controller which retains the old name, any ideas anyone?

---

