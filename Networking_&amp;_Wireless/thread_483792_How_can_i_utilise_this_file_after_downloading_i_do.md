---
title: "How can i utilise this file after downloading i dont know the commands"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by umairsaeed219 on 2007-06-25
This file is mentioned in the thread 
[http://ubuntuforums.org/showthread.php?t=471503&highlight=intel536ep](http://ubuntuforums.org/showthread.php?t=471503&highlight=intel536ep)


posted on 
[https://help.ubuntu.com/community/DialupModemHowto/Intel536EP](https://help.ubuntu.com/community/DialupModemHowto/Intel536EP)
i dont know what to do after downloading it

---

### Post by Rui Pais on 2007-06-25
Hi,
whats kind of file it is? it ends with a deb extension?

In the link you mention one are directed to a place with a downloadable:
intel536ep-feisty_2-Philippe.Vouters-23-02-2007_i386.deb

if thats the case just use your file manager (nautilus if you use gnome, konqueror, thunar if you use kde or xfce) and navigate to where your file is (home folder, desktop, whatever) and then click on file.

To do it from a terminal (in the example i asume you have it on your Desktop:
```
cd Desktop
sudo dpkg -i intel536ep-feisty_2-Philippe.Vouters-23-02-2007_i386.deb
```


hope that helps

---

