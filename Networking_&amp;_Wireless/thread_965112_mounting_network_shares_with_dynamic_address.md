---
title: "mounting network shares with dynamic address"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by DoubleMcLovin on 2008-10-31
Ok, so I want to edit my fstab to automount some network shares. I cant declare them by IP since they are dynamic, and I cant declare them by host name since I cant associate host name with a static ip in my hosts file.

so using a DYNAMIC (i dont want to change to static) address and fstab, how can I set up a share to automount? Perhaps a way to declare a string of addresses that the machine might be associated with in hosts? any ideas?

---

### Post by alienprdkt on 2008-10-31
#sudo bash
#nano -w /etc/fstab

//computername/share     /mount/point    smbfs   username=$login,password=$pass

---

### Post by superprash2003 on 2008-10-31
that could be a problem..

---

### Post by DoubleMcLovin on 2008-10-31
> **alienprdkt said:**
> #sudo bash
#nano -w /etc/fstab

//computername/share     /mount/point    smbfs   username=$login,password=$pass

This command doesnt work as I stated, because with a dynamic address and no domain affiliation, I cannot call the computer by host name on my computer at least. I receive an error saying that the IP address or host name could not be resolved.

---

