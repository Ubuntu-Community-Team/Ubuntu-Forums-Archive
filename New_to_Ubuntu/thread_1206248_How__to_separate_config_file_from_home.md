---
title: "How  to separate config file from /home"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by wariskampar on 2009-07-06
Hello, 

Everytime I upgrade my ubuntu, all the setting from the previous install will be migrated as well. This giving me headache because I can not enjoy the new feel of the new upgrade (upgrade to 9.04 to 8.10 recently). How do I separate all config file from /home? I plan to put all config in 1 dedicated partition and /home in another partition. So, in the future I can simply format / and config partition and install new upgrade on them. Please assist me. I know this can definitely be done in ubuntu but I just do know where all the config file located in ubuntu. Thanks

---

### Post by Ocxic on 2009-07-07
I don't think that is possible, your home folder holds all of your config/settings etc.. as well as your personal info, and is designed to bring your settings and preferences along with an upgrade, and is not meant to be separated.

---

### Post by CatKiller on 2009-07-07
If you want to keep personal data accessible through your Home folder but you want everything else nuked on a re-install you could have a separate partition for your personal data and then mount that to a location in your Home folder - ~/data, for example. Or mount it somewhere else and use symlinks to achieve the structure that you want - mounting it at /mnt/data and having symlinks at ~/Pictures and ~/Documents to /mnt/data/Pictures and /mnt/data/Documents, for example. You could then keep the settings that you want preserved by using symlinks for those too, like a symlink to /mnt/data/.mozilla. You'd need to keep track of which packages you had installed to re-install them in one go with the usual method.

---

### Post by frunns on 2009-07-07
Save the hidden files and folders you want to save, if any, and nuke the rest of them?

---

