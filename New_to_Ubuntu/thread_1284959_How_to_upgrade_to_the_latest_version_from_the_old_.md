---
title: "How to upgrade to the latest version from the old one"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by anuj@iit on 2009-10-07
Hi,
Right now i am using UBUNTU 8.10 version, can i upgrade to latest version online through the currently being used i.e. without formatting the old one and if yes then how?
Thanks!

---

### Post by MelDJ on 2009-10-07
go to software sources and go under the updates tab. change the  release upgrade to normal. then run update manager and you will be able to update to 9.04

---

### Post by achase79 on 2009-10-07
yes you can, you can do it from update manager, synaptic or using the following command in terminal
```
sudo apt-get dist-upgrade
```

just make sure your system is already updated beforehand and that you backup any important info. (Some people have problems with upgrading.)

---

### Post by Dougie187 on 2009-10-07
Yes. Just go into System->Administration->Software Sources and on the Updates tab make sure at the bottom the "Release Upgrade" option is set to Normal Releases.

Then if you open up the Update Manage (System->Administration->Update Manage) and hit check, it should give you a button for upgrading the system.

NOTE: Before you do this, you should make sure you backup all of your data. I have read mixed reviews for using the upgrade, and have never had it work well for me in the past, but other people have had great success with it.

---

### Post by ikisham on 2009-10-07
[https://help.ubuntu.com/community/JauntyUpgrades](https://help.ubuntu.com/community/JauntyUpgrades)

---

