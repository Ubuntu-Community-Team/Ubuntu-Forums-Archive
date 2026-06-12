---
title: "upgrading"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by rickmoy on 2009-10-20
I want to upgrade from 9.04 to 9.10 that will be released soon. i run ubuntu inside windows. will that create a problem? do i need to backup my files?thanks.

---

### Post by Peter09 on 2009-10-20
Its always worth backing up any data that you cannot afford to lose. After that upgrade will work. It is worth noting that karmic uses a new file system ext4, and a new bootloader. These won't be installed on an update, only on a new install.

---

### Post by MelDJ on 2009-10-20
keep your files in the hosts folder before you upgrade in case something happens

---

### Post by dvlchd3 on 2009-10-20
This depends.  When the stable version is released on the 29th the Update Manager in Ubuntu will tell you there is a release available and if you want to upgrade.  This will allow you to upgrade to 9.10 without removing any configurations, files, applications, etc you already have.

Some people, myself included, prefer to do a fresh install.  This will ensure that EVERYTHING is upgraded to the new version.  Some things (like GRUB 2) cannot be upgraded, they must be freshly installed.  If this is the route you prefer, you will need to backup all your files, and make sure you know all the packages/applications you had installed before you "upgrade".

Hope this helps.

---

### Post by swoody on 2009-10-20
While it is true that Grub2 and ext4 won't be created on an upgrade from an existing install, does not mean that they cannot be upgraded manually. There are many ways to get to the same destination, just be sure to make backups first, and go with what is most comfortable for you :)

---

### Post by konqueror7 on 2009-10-20
as they said, if you want all of the features of 9.10, then do a clean install. if you don't really need these features such as grub2 or ext4 (you can convert your current ext3 to ext4 without doing a fresh install), then just do a normal upgrade, but be aware that there are a few probable complication with the upgrade especially regarding configurations.

my advice would be, wait for 1 week after 9.10 release, this will give it enough time to at least fix some new found (critical) defects, and do a clean install.

---

