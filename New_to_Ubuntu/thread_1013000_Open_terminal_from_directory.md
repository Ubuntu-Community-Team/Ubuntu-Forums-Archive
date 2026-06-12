---
title: "Open terminal from directory"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by propagation_of_sound on 2008-12-16
I'm new to Ubuntu, and, bit by bit I'm getting the hang of it. What really bugs me though is that, as I prefer graphical environments as I migrated from Windows, I'm browsing my files using Nautilus and want to execute a command on a file in that folder. Currently I'm opening up terminal and navigating again to that directory, but is there a way to in nautilus open up a terminal window that is already navigated to that directory?

If there isn't, I think it would be a great feature, as many people I know would like to migrate from Windows but are scared of spending aeons typing in long addresses to get to their hidden system files etc. (that and their phobia of the terminal prompt). 

Thanks in advance.

---

### Post by Tatty on 2008-12-16
I believe

```
sudo apt-get install nautilus-open-terminal
```  may do that for you.

---

### Post by SpenceMakesSense on 2008-12-16
well you can drag the file into the terminal. So if you wanted to open a file with python you can type
```
 python(drag .py file here)
```

Other then that the only way I know of to get to a specific file is to type the route to it (/home/user/documents/homework.doc)

---

### Post by wolfen69 on 2008-12-16
if you do ```
gksudo nautilus
``` it will open nautilus as a superuser and you will be able to make changes to files. just be careful what you edit.

---

### Post by Hospadar on 2008-12-16
You also might be interested in the "nautilus-gksu" package to run/open stuff as root from a nautilus window

---

### Post by deputy on 2008-12-16
I recommend installing UbuntuTweak. It has a nice GUI interface to tweak several Ubuntu settings and installing Nautilus scripts such as Open Terminal in Current Dir. [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

