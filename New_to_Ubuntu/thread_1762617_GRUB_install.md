---
title: "GRUB install"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by neil_1 on 2011-05-19
when doing a clean install of ubuntu 11.04 (i have 10.04 now), do i have to install GRUB again or do i uncheck it in the installer ?

---

### Post by oldfred on 2011-05-19
It will install the newest version of grub.

Have you backed up all your current data. Or have a separate /home? Did you make a list of installed applications to make it easy to reinstall? Have you made any system wide custom changes that might be in /etc and backed those up also?

---

### Post by neil_1 on 2011-05-19
> **oldfred said:**
> It will install the newest version of grub.

Have you backed up all your current data. Or have a separate /home? Did you make a list of installed applications to make it easy to reinstall? Have you made any system wide custom changes that might be in /etc and backed those up also?
ive backed up everything on an external HDD,
no i dont have a separate /home
i didnt make any /etc changes

---

### Post by oldfred on 2011-05-19
You might want to do this:

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

dpkg --get-selections > ~/my-packages
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade

---

### Post by neil_1 on 2011-05-20
alright , so i have to install the new grub ?

---

### Post by garvinrick4 on 2011-05-20
> alright , so i have to install the new grub ?Yes you do, when computer boots up it looks for grub files in the partition or install you are using to boot with.

---

