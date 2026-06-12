---
title: "Is an Application installed?"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by held7over on 2009-10-14
In Mandriva I could type "rpm -q <application name>" on the commandline and it would tell me if it was installed. I have been looking for a similar command in apt but haven't found one yet.

What do you guys use to check via commandline if something is installed without trying to install it?

Thanks! :)

---

### Post by Rocket2DMn on 2009-10-14
Sure,
```
apt-cache policy <package>
```
That will show the installed version and the version in the repositories.

---

### Post by oldos2er on 2009-10-14
dpkg-query -s <package name>

---

### Post by dominiquec on 2009-10-14
dpkg -l gives you the list of all APT-installed applications on your system.

---

### Post by held7over on 2009-10-14
Thanks!  Those overflow my cup quite well! :P

---

