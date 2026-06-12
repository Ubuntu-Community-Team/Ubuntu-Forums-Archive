---
title: "having problems with ubuntu software center"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by smellslike on 2010-12-17
Im having problems with my software center it says
"Items cannot be installed or removed until the package catalog is repaired" and then i press repair and then it says "the installation or removal of a software package failed" when i click details it says 

installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 171230 files and directories currently installed.) 
Removing usplash-smooth ... 
 Removing any system startup links for /etc/init.d/usplash-smooth-set ... 
 Removing any system startup links for /etc/init.d/usplash-smooth-get ... 
update-alternatives: error: no alternatives for usplash-artwork.so. 
dpkg: error processing usplash-smooth (--remove): 
 subprocess installed post-removal script returned error exit status 2 
Processing triggers for ureadahead ... 
Errors were encountered while processing: 
 usplash-smooth

Any help would be greatly appreciated and im totally new too linux so if you explain it like you are talking to child that would be excellent too! 

Cheers :-D

---

### Post by ajgreeny on 2010-12-17
See if running the command ```
sudo apt-get clean
``` which will remove packages from the cache in /var/cache/apt/archives helps.

---

### Post by smellslike on 2010-12-17
> **ajgreeny said:**
> See if running the command ```
sudo apt-get clean
``` which will remove packages from the cache in /var/cache/apt/archives helps.


Thanks for you quick response!! Unfortunately the command didnt help because its still saying the same thing. Any other ideas?

---

### Post by sikander3786 on 2010-12-18
Applications > Accessories > Terminal:

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update && sudo apt-get upgrade
```

Please post the output for each of those commands. And while posting, click the # icon in post menu and paste your text in between the generated code tags.

---

### Post by nei_non on 2011-07-24
See If you have a broken package (or more). Open synaptic and use filter "broken". Locate (if there are any), the broken package and try to reinstall or remove them, then run again :

```
sudo apt-get update && apt-get upgrade
```

---

### Post by amjjawad on 2011-07-24
> **sikander3786 said:**
> Applications > Accessories > Terminal:

```
sudo apt-get install -f
``````
sudo dpkg --configure -a
``````
sudo apt-get update && sudo apt-get upgrade
```Please post the output for each of those commands. And while posting, click the # icon in post menu and paste your text in between the generated code tags.

+1

By the way, how are you, sikander ;)

---

### Post by XubuRoxMySox on 2011-07-24
Actually there may be a bug in the Ubuntu Software Center. A program that I installed using the Software Center failed to run and put a li'l blip in the center of my screen. So I removed it using the Software Center and tried again, same result.

So I opened Synaptic, installed my desired software (which went perfectly), and removed the Ubuntu Software Center.

-Robin

---

