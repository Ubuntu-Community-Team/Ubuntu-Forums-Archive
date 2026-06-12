---
title: "Not enough space on drive C:/ ?"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by Grimofnight on 2010-01-08
I have a little over 30gb of free space on my hard drive. I've tried two different games. Spider-man 3 the movie: The game and The chronicles of riddick: Assault on dark athena. Spider-man game uses up 6000mb of space and Chronicles of Riddick uses a little over 10gb of space. Is there a way to access the free space? 

Also i am using Ubuntu 9.10 and i've been using the the wine program. Chronicles of riddick and spiderman game will allow me to get to the custom or easy installation on install shield wizard. Using either option still renders me the same outcome with no space available on drive C:/. Any one run into this problem before or have a quick fix for it?

---

### Post by cariboo on 2010-01-08
Wine drive C:/ is located in your home Directory. If you aqhve a seperate home directory yo may want to make it a bit larger by using the Live CD and the partition editor. If you installation is all on one partition you may need to remove archived packages that are in /var/cache/apt/archives. To do this open an Applications-->Accessories-->Terminal and type:

```
sudo apt-get autoremove
```

the above command removes unneeded dependencies, then in the same terminal type:

```
sudo apt-get clean
```

This command removes archived files from /var/cache/apt/archives. 

Also check your trash, there may be a lot of files in there.

---

