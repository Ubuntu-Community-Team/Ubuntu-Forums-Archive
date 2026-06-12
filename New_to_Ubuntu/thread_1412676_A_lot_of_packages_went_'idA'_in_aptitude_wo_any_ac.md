---
title: "A lot of packages went 'idA' in aptitude w/o any actions"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by karatedog on 2010-02-21
I was firing up aptitude to install some app, but as I got used to the package removal feature of aptitude, just pressed 'g'. I just freaked out when it gave me a lot of purple lines with the status code 'idA' and wanted to remove them as they were not needed (620 packages). These included: apache, putty, mysql, cairo-dock, dozens of KDE packages and a lot of vital elements to my system, all of them being the actual installed versions. 

Synaptics listed these packages for autoremoval, but defined no default action to them (whereas aptitude would have removed them).

I was expecting the worst so I made a list of the would-be-purged packages with 'apt-get purge' to reinstall them later, but I was a coward :D and pressed '+' on the not-needed packages, effectively reinstalling them and removing the 'A' flag.

I'm absolutely clueless on what happened.

---

