---
title: "Moving Mail directory"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by Driventemple on 2009-03-09
Hi,

Just installed 8.10 and am busy transferring all data. I wish to copy the Mail directory from /user into /etc/thunderbird/profiles.

I am told I do not have correct permissions.  Used chown-r to change ownership from /etc/thunderbird on but permissions stop at thunderbird.

Tried to chown /etc/thunderbird/profiles but this does not work.

Anybody help please?

---

### Post by taurus on 2009-03-09
```
gksudo nautilus
```
or
```
sudo mv directory /etc/thunderbird/profiles
```

---

### Post by Driventemple on 2009-03-09
Thanks,

Tried that command but didn't work.  Tried:
mkdir: cannot create directory `Mail': Permission denied

The icon for profile has a padlock on it.  How do I set the permissions to allow me to read and write within in?

---

### Post by Driventemple on 2009-03-09
Sorry, Nautilus DID work!  The directory is where it should be but I'm not seeing my old Inbox..

---

