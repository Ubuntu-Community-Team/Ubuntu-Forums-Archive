---
title: "Deluge package conflicts with Colibri"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by Falc7 on 2010-04-18
Hi
I like the KDE Colibri notifications a lot
[http://kde-apps.org/content/show.php/Colibri?content=117147](http://kde-apps.org/content/show.php/Colibri?content=117147)
But the problem i have is that Colibri conflicts with the package, 'notification daemon', which is required by deluge, which i also like.

Now according to this page:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=570606](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=570606)

Notification daemon isen't vital to the way deluge works, is there a way i can run deluge without the package notification-daemon installed?
I am using deluge 1.2.3

---

### Post by sandyd on 2010-04-18
> **Falc7 said:**
> Hi
I like the KDE Colibri notifications a lot
[http://kde-apps.org/content/show.php/Colibri?content=117147](http://kde-apps.org/content/show.php/Colibri?content=117147)
But the problem i have is that Colibri conflicts with the package, 'notification daemon', which is required by deluge, which i also like.

Now according to this page:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=570606](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=570606)

Notification daemon isen't vital to the way deluge works, is there a way i can run deluge without the package notification-daemon installed?
I am using deluge 1.2.3
remove colbri, install notification-daemon
then download the attachment to your desktop (I extracted it from the colibri deb)
(replace *username* with your username)
```

kdesudo ark /home/*username*/Desktop/data.tar.gz

```theirs no preinstall scripts, postinstall scripts, or any scripts at all, so just extract the "usr" folder thats inside the archive into /
done.

you can also install notification-daemon and "sudo dpkg --force all" the colbri deb.

another way would be to create a dummy deb for notification-daemon (a dummy deb has nothing inside of it) and make it like version 5000 (or if deluge requires a certain version, just make a dummy deb for the version it needs). The version in the repos will never catch up, and you can easily install deluge without issues.

---

### Post by Falc7 on 2010-04-18
I used your first method and its working great, thanks :)

---

