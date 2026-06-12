---
title: "need help deleting/moving a file"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by Dr.Grumbles on 2009-04-20
I used terminal to install wolfenstein enemy territory 2.60, but installed it to /usr/local/games instead of /usr/games
im a newb when it comes to linux but so far i am really enjoying it, but the problem im having is that i downloaded a patch for the game [2.60b] and what i have to do is just replace a few files in the game folder, but since it is installed in this other directory, i cant access it.  i have tried a lot of things and seen a lot about how to login as root, but nothing has worked yet.  im trying to copy it to my usr/games folder so i can edit it and hopefully access it from gnome's games menu.

any ideas?

---

### Post by _Purple_ on 2009-04-20
You can open the GUI with admin access with the following command 
```
gksu nautilus
``` 

Be careful as you will have the admin privilege. Similarly you can use command line. 
To copy files
```
sudo cp /path_to_your_file/filename /usr/game/filename
```

To move files
```
sudo mv /path_to_your_file/filename /usr/game/filename
```

To delete files
```
sudo rm /usr/game/filename
```

Replace path_to_your_file with the actual path and filename with your filename.

---

