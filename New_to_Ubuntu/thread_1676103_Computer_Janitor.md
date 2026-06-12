---
title: "Computer Janitor"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by manish411 on 2011-01-26
I have Computer Janitor installed . But how to use it to refresh my computer??

---

### Post by davidmohammed on 2011-01-26
not sure what you mean "refresh" - I presume you mean clean up old packages etc.

In that case, I would avoid computer janitor like the plague!

Use [Ubuntu Tweak]("http://ubuntu-tweak.com/") - my easier to use and I've never had any issues with its "cleaning" abilities.

---

### Post by Frogs Hair on 2011-01-26
When you press do selected tasks it will remove the items with a check next to them . Be very certain that you know what you are deleting . If your not sure remove the check from the box before continuing .

I prefer BleachBit from the software center and you can also set the synaptic package manager to delete downloaded updates after installed from the Settings > Preferences> Files tab.

---

### Post by garvinrick4 on 2011-01-26
I use aptitude instead of apt-get and it seems to keep things tidy:
sudo apt-get install aptitude
sudo aptitude update && sudo aptitude safe-upgrade
Lets me know what is going on with packages:
There is also autoclean that is worth a read:

---

