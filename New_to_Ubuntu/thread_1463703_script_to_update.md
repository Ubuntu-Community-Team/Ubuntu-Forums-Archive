---
title: "script to update"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-04-27
#! /usr/bin/bash
sudo apt-get update
echo acer 
sudo apt-get dist-upgrade -y echo acer


how do i make this change so that my sudo password is entered so that i dont have to type it for the script to run under a normal user. I will be the only user using this script.

---

### Post by mikewhatever on 2010-04-27
Just run the script as super user, and get rid of the sudo`s inside.

---

### Post by aeiah on 2010-04-27
run it in root's crontab instead of you users (with sudo removed like was suggested). you can also pass the password to sudo but this isn't very secure since the password will be stored in the script. you can do it with
```

echo "password" | sudo -S command

```

but it is **not** recommended!

---

### Post by lance bermudez on 2010-04-27
could i just use scheduled tasks form the gnome to add the commands to cron? it says something about only user in this dir commands will be done or something like that.

---

