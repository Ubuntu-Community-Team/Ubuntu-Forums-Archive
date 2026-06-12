---
title: "Ubuntu 10.10 froze when I tried to upgrade to 11.4 and I rebooted and now it's screwd"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by Kururu Souchou on 2011-04-15
my computer is a Ubuntu 10.10 64bit and it froze during a distribution upgrade at the installing sudo part and now it won't boot correctly

---

### Post by NightwishFan on 2011-04-15
For future reference please wait at least 24 hours before bumping your posts. Just hold tight, someone will get back to you! :)

1. Try booting into recovery mode. If you do not know how: You can hold shift right after the bios screen and you will get a menu with options to boot Ubuntu or Ubuntu (Recovery Mode). If you normally see this menu (such as with a dual boot with Windows) you do not need to hold shift.

2. Once you get to recovery mode ensure you have a wired connection and choose "root prompt with networking".

3. Type this command exactly: ```
dpkg --configure -a && apt-get -f install && apt-get install ubuntu-desktop
```

---

### Post by Kururu Souchou on 2011-04-15
> **NightwishFan said:**
> For future reference please wait at least 24 hours before bumping your posts. Just hold tight, someone will get back to you! :)

1. Try booting into recovery mode. If you do not know how: You can hold shift right after the bios screen and you will get a menu with options to boot Ubuntu or Ubuntu (Recovery Mode). If you normally see this menu (such as with a dual boot with Windows) you do not need to hold shift.

2. Once you get to recovery mode ensure you have a wired connection and choose "root prompt with networking".

3. Type this command exactly: ```
dpkg --configure -a && apt-get -f install && apt-get install ubuntu-desktop
```
but i don't have wired, wire not long enough

---

### Post by Kururu Souchou on 2011-04-15
> **NightwishFan said:**
> For future reference please wait at least 24 hours before bumping your posts. Just hold tight, someone will get back to you! :)

1. Try booting into recovery mode. If you do not know how: You can hold shift right after the bios screen and you will get a menu with options to boot Ubuntu or Ubuntu (Recovery Mode). If you normally see this menu (such as with a dual boot with Windows) you do not need to hold shift.

2. Once you get to recovery mode ensure you have a wired connection and choose "root prompt with networking".

3. Type this command exactly: ```
dpkg --configure -a && apt-get -f install && apt-get install ubuntu-desktop
```
but i don't have wired, wire not long enough
im in livecd

---

### Post by NightwishFan on 2011-04-15
> **Kururu Souchou said:**
> but i don't have wired, wire not long enough

Try without the wire anyway. You might have all the packages you need already in the cache. You can use root prompt instead of net root. Either one is fine if you do not have a wired connection.

---

### Post by Kururu Souchou on 2011-04-18
> **NightwishFan said:**
> Try without the wire anyway. You might have all the packages you need already in the cache. You can use root prompt instead of net root. Either one is fine if you do not have a wired connection.
When i thype anything to do wit dpkg or apt-get, it says im not allowed to write on the drive. sorry, he keyboards at schoolr sticky, so i won't be typing for long
i fresh installed anyways
by , the teacher's coming

---

