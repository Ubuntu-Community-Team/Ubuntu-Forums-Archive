---
title: "trying to find a repository for winetricks"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by tysonh80 on 2011-03-28
using ubuntu 10.10.  I found a repository through a google search.  I know how to add repositories but when I enter the information into the field the add button is grayed out and doesn't allow me to enter add the repository.  I need winetricks so I can run internet explore for some work my wife does online that only supports that browser.  

Ive done some searching around but haven't found the right repository yet.

thanks in advance

---

### Post by Enigmapond on 2011-03-28
Open the terminal and do:

```
sudo add-apt-repository ppa:ubuntu-wine/ppa 
sudo apt-get update
sudo apt-get install winetricks
```

(Assuming you are using 10.04 or 10.10....)

---

### Post by tysonh80 on 2011-03-28
thank you very much.

worked like a charm

---

### Post by Enigmapond on 2011-03-28
My pleasure.. :)

You should mark the thread as solved in the Thread Tools..

Cheers!

---

