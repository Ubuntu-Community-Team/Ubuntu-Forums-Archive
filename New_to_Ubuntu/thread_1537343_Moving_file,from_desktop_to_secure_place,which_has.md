---
title: "Moving file,from desktop to secure place,which has only root permission"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by himangsu on 2010-07-23
I install latest version of flashplayer,by downloading as .tar.gz file,and extracting it into .so file,placing it in home folder,and by running a command like 
sudo cp /home/user_name/libflashplayer.so /usr/lib64/mozilla/plugins
flashplayer is running well,but now i find a folder in my desktop like 
flash-pluging-10.1.53.64
which neither be moved,nor be deleted. only permission is to the root.
how can i shift it to the secure place if it is important file? Or how can delete it if it is not necessary for my coomputer? Please help me..........

---

### Post by nidzo732 on 2010-07-23
what's in the folder

---

### Post by anon.jdh on 2010-07-23
```
sudo rm ~/Desktop/flash-pluging-10.1.53.64
```

If it's already installed and running, you just have to remove the file.

If you're paranoid just run this one:

```
sudo chmod 777 ~/Desktop/flash-pluging-10.1.53.64
```

and move it to wherever you want.

---

