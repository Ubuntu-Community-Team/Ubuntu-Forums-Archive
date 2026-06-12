---
title: "Selecting Locale files"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by gcampbell86 on 2009-06-12
I'm trying to install compizconfig, but in the terminal it is telling me about configuring localepurge and that I have to select locale files, i see that its for languages, what do i need to check for the UK?

Thanks

---

### Post by Mornedhel on 2009-06-12
Are you trying to install compizconfig from sources or an external archive ?

The recommended way is to install it from the repositories with :

```
sudo apt-get install compizconfig-settings-manager
```

Or you can use any package manager of your choice (Synaptic, ...)

---

### Post by gcampbell86 on 2009-06-12
As i'm new to all this, I was just using the instructions on  [https://help.ubuntu.com/community/SettingUpUbuntu](https://help.ubuntu.com/community/SettingUpUbuntu)

---

### Post by gcampbell86 on 2009-06-12
The file attached is what it has come up with.  Any suggestions

---

### Post by Mornedhel on 2009-06-12
Yes, that page recommends installing localepurge among other things. localepurge is, according to its package description,

```
a hack which is *not* integrated with
 Debian's package management system and therefore is not for the faint
 of heart. This program interferes with the Debian package management
 and does provoke strange, but usually harmless, behaviour of programs
 related with apt/dpkg like dpkg-repack, debsums, reportbug, etc.
 Responsibility for its usage and possible breakage of your system
 therefore lies in the sysadmin's (your) hands.

```I would not recommend installing localepurge unless you know what it does and are convinced that you need it. The rest of the packages are not all needed either. A short and safe version of the apt-get command in the middle should be :

```
sudo apt-get install ubuntu-restricted-extras vlc compizconfig-settings-manager rar unrar-free flashplugin-nonfree gparted
```I have removed from that list several applications that are either specialized or intended for power users.

Your locale should be en_GB (not sure but fairly reasonably certain).

---

