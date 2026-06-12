---
title: "the location of the  deb files"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2010-04-03
where are the deb files stored in the files system which are downloaded and installed through the terminal?????

---

### Post by TheNerdAL on 2010-04-03
> **DavidTangye said:**
> Start Synaptic, go to the Preferences, and in the Files tab I think you will see that the .debs are set to be deleted on install. Change this option to what you want.
That might help.

---

### Post by azertyh on 2010-04-03
it's not in /var/cache/apt/archives?

---

### Post by @rizz on 2010-04-03
kool question!!!!

 here the answer!

[http://ubuntuforums.org/archive/index.php/t-231789.html](http://ubuntuforums.org/archive/index.php/t-231789.html)


if your packet manager is not configured to delete files after the installation they will remain the cache.
```
 $ ls /var/cache/apt/archives/
```

cheers!:popcorn:

---

### Post by karthick87 on 2010-04-03
How to configure packet manager,to store the downloaded files in cache?

---

### Post by @rizz on 2010-04-03
Easy steps

 1) Click on system menu

 2) Click on Administration

 3) Select Synaptic Packet manager

 4) Click on setting at the top

 5) Select preferences

 6) click on files tab

 7) Select the option that says "leave all downloaded packages in the cache"

 8) Click apply and then ok!

 That Does the trick i guess........

 You can also check the repositories under the preference for more advanced options

---

