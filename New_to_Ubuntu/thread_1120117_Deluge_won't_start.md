---
title: "Deluge won't start"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by alanfang on 2009-04-08
Deluge suddenly stopped starting. I try to run it, the window for starting comes up, and then  after 10 seconds goes away. I tried uninstalling it several times, to no avail.

---

### Post by durand on 2009-04-08
Open a terminal (Applications > Accessories > Terminal) and run:
```
deluge -u gtk
```

Post what it outputs here using quote tags.

---

### Post by alanfang on 2009-04-08
Usage: deluge [options] [torrents to add]

deluge: error: no such option: -u

---

### Post by durand on 2009-04-08
Oh right, you have an older version of deluge.

Just run deluge on its own.

---

### Post by alanfang on 2009-04-08
huh? From the command line?

---

### Post by durand on 2009-04-08
You might want to update to the latest version. This would be the easiest way:

1. Go to [https://edge.launchpad.net/~deluge-team/+archive/ppa](https://edge.launchpad.net/~deluge-team/+archive/ppa) and copy the apt sources.list entries.
2. Open sources.list with sudo gedit /etc/sources.list
3. Paste the lines at the bottom of the file.
4. Save it and exit.
5. In the terminal, run **sudo apt-get update; sudo apt-get install deluge**

That should give you the latest version which has a completely different architecture and it's much nicer to use :)

---

### Post by durand on 2009-04-08
Yeah. It will output errors which might help you understand why deluge stops running.

---

### Post by lovinglinux on 2009-04-08
If you were using the blocklist plugin, try deleting ~/.config/deluge/blocklist.cache and ~/.config/deluge/blocklist.conf and start it again. This happened to me last week and the culprit was the blocklist file.

---

