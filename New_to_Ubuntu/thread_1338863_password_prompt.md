---
title: "password prompt"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by iRounak on 2009-11-26
I want to disable password prompts for opening any partition on the same hard disk as on which Ubuntu is installed or any other hard disk.

---

### Post by cariboo on 2009-11-26
Basically you can't, as normal user, you can only manipulate files in your home directory. In order to do the same in any folder you aren't the owner of, you need to be root, that's why you need to enter your password.

Have a look [here]("http://https://help.ubuntu.com/community/RootSudo") for more info.

---

### Post by iRounak on 2009-11-29
the link ([http://www.devices.com/help.ubuntu.com/community/RootSudo](http://www.devices.com/help.ubuntu.com/community/RootSudo)) you gave is dead.
I just want to know if I can use the partitions without the password prompt and without logging in as root.

---

### Post by ubudog on 2009-11-29
> **iRounak said:**
> the link ([http://www.devices.com/help.ubuntu.com/community/RootSudo](http://www.devices.com/help.ubuntu.com/community/RootSudo)) you gave is dead.
I just want to know if I can use the partitions without the password prompt and without logging in as root.

No, you will need to be root.

---

### Post by jrrader on 2009-12-01
I realize there are rules against writing tutorials on how to log in as root, but I don't see anything on the "sudoroot" page or "forum policy on log-in-as-root page" that says we can't help someone change the policykit to fit their needs better.

This is an easy fix. Open terminal:

```
gksudo gedit /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy
```

locate org.freedesktop.devicekit.disks.filesystem-check-system-internal within that file and change (line 34) "<allow_active>auth_admin_keep</allow_active>" to

```
<allow_active>yes</allow_active>
```

Save and it should work.  Keep in mind that this will allow all users of your computer to mount internal partitions.  If you are the only user, or your don't care if others access those partitions, then it's not really an issue.  If you have Windows on one of those partitions, you are basically giving anyone with an Ubuntu account full access to every file you have on windows. If you need a more secure way, you can create an exception in /etc/PolicyKit/PolicyKit.conf to allow only you to mount partitions.  To learn how to do this, type "man policykit.conf" in terminal.

Alternately, and I'm surprised no one suggested this, you can use the file /etc/fstab to automount a partition.  If it is an NTFS filesystem, download and run ntfs-config from synaptic.  If it is something else, learn how to write an entry from this page: 
[http://www.cae.wisc.edu/linfstab](http://www.cae.wisc.edu/linfstab)

---

### Post by iRounak on 2009-12-01
> locate org.freedesktop.devicekit.disks.filesystem-check-system-internal within that file and change (line 34) "<allow_active>auth_admin_keep</allow_active>" to
Many thanks, jrrader. It did work. May I also bother you with [http://ubuntuforums.org/showthread.php?p=8407993](http://ubuntuforums.org/showthread.php?p=8407993)
(I do not want password prompt at startup but I still want my keyring to be unlocked.)

---

### Post by lisati on 2009-12-01
> **iRounak said:**
> the link ([http://www.devices.com/help.ubuntu.com/community/RootSudo](http://www.devices.com/help.ubuntu.com/community/RootSudo)) you gave is dead.
I just want to know if I can use the partitions without the password prompt and without logging in as root.

Corrected link: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

