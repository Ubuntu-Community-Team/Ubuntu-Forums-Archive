---
title: "Troubling updating"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by SW90 on 2010-02-20
I've been trying to update, but I get this message

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) hardy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://cudlug.cudenver.edu](http://cudlug.cudenver.edu) hardy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

what should i do?

---

### Post by cariboo on 2010-02-20
Open a terminal and type the following commands:

```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```

Press enter after each command.

---

### Post by SW90 on 2010-02-20
I got this: (and this is with the ubuntu installation cd inserted)

W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
sarah@sarah-desktop:/var/lib/apt$

---

