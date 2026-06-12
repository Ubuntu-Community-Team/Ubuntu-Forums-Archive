---
title: "Upgrade to Ubunbtu 10.10; Partitions"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by UtahApocalypse on 2010-10-14
I would like to know how to make sure my /home is on the right partition so I can perform an upgrade to my o/s without losing data. I currently am using LinuxMint.

---

### Post by SpockVulcan on 2010-10-15
You will have to back up only what is important because preserving all of your home partition from Linux Mint to Ubuntu will mess up menus, apps, settings... it needs to be formatted when installing Ubuntu.

---

### Post by coffeecat on 2010-10-15
> **UtahApocalypse said:**
> I would like to know how to make sure my /home is on the right partition so I can perform an upgrade to my o/s without losing data.

Post the terminal output of:

```
df -h
```

That will tell us

> **SpockVulcan said:**
> You will have to back up only what is important because preserving all of your home partition from Linux Mint to Ubuntu will mess up menus, apps, settings... it needs to be formatted when installing Ubuntu.

Are you sure? Even the unique Mint Menu uses the same configuration as the standard gnome menu. If the worst happened the OP could delete the hidden configuration files/folders that are causing problems and these would be regenerated with defaults at the next gnome login. The menu might be more of a challenge though.

---

### Post by srs5694 on 2010-10-15
> **SpockVulcan said:**
> You will have to back up only what is important because preserving all of your home partition from Linux Mint to Ubuntu will mess up menus, apps, settings... it needs to be formatted when installing Ubuntu.

That's not really true. There may be some incompatibilities between Mint's icons, menus, etc. and Ubuntu's, but I'd expect most icons, menus, and so on would continue to work. If they don't, it's always possible to create a new account or create a new home directory and then just move all your non-configuration files to the new home directory (moving within a filesystem takes almost no time). This will be much faster and safer than backing up and restoring more than a trivial amount of data.

---

### Post by scrooge_74 on 2010-10-15
make a new partition, then move /home there, then reinstall

---

