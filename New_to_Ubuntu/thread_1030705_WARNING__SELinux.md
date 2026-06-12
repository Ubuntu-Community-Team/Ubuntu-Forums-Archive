---
title: "WARNING **: SELinux"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by DforVendetta on 2009-01-04
What does this mean?

(gnome-system-monitor:3011): WARNING **: SELinux was found but is not enabled.

google says selinux is security. If I have it I'd like it to be enabled..

---

### Post by cariboo on 2009-01-04
Ubuntu uses Apparmor for program level security, instead of Selinux. Have a look [here]("http://ubuntuforums.org/showthread.php?t=1008906"), for an introduction to Apparmor.

Jim

---

### Post by amauk on 2009-01-04
SELinux is not used in Ubuntu (as far as I know, anyway)
a similar system, called AppArmor is used in it's place

Don't worry about it


*edit*
too late

---

### Post by DforVendetta on 2009-01-04
wow, google doesn't have **** on the people in this forum. That was fast, thanks.

---

### Post by mcduck on 2009-01-04
SELinux is *more* security, meaning something around level of security suitable for organizations like U.S: National Security Agency (which is a major contributor to SELinux)..

It's probably a way more security than what any normal user needs. Ubuntu is pretty much secure enough for all your needs unless you really are running a large organization that handles top secret stuff. :D

[http://en.wikipedia.org/wiki/Security-Enhanced_Linux]("http://en.wikipedia.org/wiki/Security-Enhanced_Linux")

---

