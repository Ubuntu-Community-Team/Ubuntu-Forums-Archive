---
title: "Squirrelmail can't find config.php after update"
date: 2022-12-15
forum: Networking &amp; Wireless
---

### Post by ese002 on 2022-12-15
A recent upgrade to 22.04.1 LTS somehow broke Squirrelmail.

Logins are met with this fun message.[B]
ERROR:[/B] Config file ' .        '"config/config.php" not found. You need to ' .        'configure SquirrelMail before you can use it.
';    exit;}// If we are, go ahead to the login page.header('Location: src/login.php');?>

The thing is, I HAVE a well tested /etc/squirrelmail/config/config.php and /usr/share/squirrelmail/config is linked to /etc/squirrelmail

It worked before the upgrade.  Is the update looking for it somewhere else?   If so, where?

---

