---
title: "Network Manager Hosed--by Vista!!!!"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by Peter108 on 2007-08-03
Stranger than truth.  Using [Broadcom Howto]("http://ubuntuforums.org/showthread.php?t=185174") I got my wireless up and running.  I also installed network manager.  In logging in I am prompted to "Enter password for default keyring to unlock".   Using PasswordSafe on my Vista machine I generated a random password and was using that last night.  But I forgot to save the password.  Overnight, Windows crashed, I lost the password, I don't remember it, and today I can't get into network manager.:mad: I uninstalled it using apt-get from the shell, rebooted, and am still being prompted as follows:

Enter password for default keyring to unlock
The application nm-applet (/usr/bin/nm-applet) wants access to the default keyring but it is locked.

Help!

Peter

---

### Post by Peter108 on 2007-08-03
I should add that I uninstalled and RE-installed Network Manager, in case that wasn't obvious.

---

### Post by jay019 on 2007-08-03
Have you tried uninstalling reinstalling the gone-keyring-manager? Not sure if it will do the trick, but maybe worth a try.

---

### Post by noob12 on 2007-08-03
Don't remove software and reinstall.  You can remove your default keyring and restart.  A new one will be created.

This command [COLOR="Red"][B]will remove your default gnome keyring
and all keys you had saved in it.[/B][/COLOR]
```

rm ~/.gnome2/keyrings/default.keyring

```

---

### Post by Peter108 on 2007-08-03
Thanks, noob12.  I'm a noob myself, and appreciate the quick reply.

---

