---
title: "Update/Upgrading Ubuntu 9.04"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Evilhugbear on 2009-04-26
Hello, I have been trying to update my ubuntu to see if there are any updates available. I have searched on google how to and it says type : apt-get update into terminal. After i do this it says [COLOR=#009900]E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory. [COLOR=Black]And then when i tried to do apt-get upgrade it asked if i am root, which I am not sure if I am.

Is This the right way to update/upgrade Ubuntu 9.04?

Also, How do I make myself root?

Please Help!
[/COLOR][/COLOR]

---

### Post by steve101101 on 2009-04-26
> **Evilhugbear said:**
> Hello, I have been trying to update my ubuntu to see if there are any updates available. I have searched on google how to and it says type : apt-get update into terminal. After i do this it says [COLOR=#009900]E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory. [COLOR=Black]And then when i tried to do apt-get upgrade it asked if i am root, which I am not sure if I am.

Is This the right way to update/upgrade Ubuntu 9.04?

Also, How do I make myself root?

Please Help!
[/COLOR][/COLOR]

sudo apt-get update. sudo runs the following command with root permissions.

---

### Post by steve101101 on 2009-04-26
to upgrade to jaunty:

To upgrade from Ubuntu 8.10, press Alt+F2 and type in “update-manager -d” (without the quotes) into the command box.

---

### Post by sylvainrb on 2009-04-26
Enter the following in the terminal
```
sudo aptitude update

```
and then you can select the update manager in the notification area on your panel or run
```
sudo aptitude dist-upgrade
```

---

### Post by Evilhugbear on 2009-04-26
thanks i got it :P

---

