---
title: "Install LXDE, remove Gnome"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by JoeNZ on 2010-02-06
Hello from NZ,

I have just installed LXDE, how do i remove Gnome so my Ubuntu is just LXDE?

Kind Regards

JoeNZ

---

### Post by mushwars on 2010-02-06
[s]you need to change your .xinitrc file to execute LXDE's startup script which I dont know what that is.[/s] You dont want to remove gnome untill your are sure you are happy with LXDE. its good to have it to fall back on.

I am sorry I guess ubuntu doesnt use the .xinitrc file. I will do a little research real fast on how to get startx to start your new window manager on ubuntu.

I would reccomend you to look at [http://google.com/](http://google.com/)

---

### Post by JoeNZ on 2010-02-06
I have restarted the machine and logged on to the LXDE session. Just wondering about how to remove Gnome.

---

### Post by mushwars on 2010-02-06
oooo thats nice, it does it automatically, that is whats nice about debian and gdm.

```
sudo apt-get purge gnome
sudo apt-get autoremove
```


read this before you do that
[http://ubuntuforums.org/showpost.php?p=2257985&postcount=2](http://ubuntuforums.org/showpost.php?p=2257985&postcount=2)

---

### Post by kidux on 2010-02-06
Be very careful before removing the gnome desktop because it has some wonky dependencies (evolution anyone) and a program you like may not function correctly or just plain not be there anymore.

---

### Post by snowpine on 2010-02-06
Follow the "Remove Ubuntu" directions, but replace "xubuntu-desktop" with "lxde":

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

You will probably have to reinstall some of the applications you want to keep.

---

### Post by JoeNZ on 2010-02-07
I tried the "sudo apt-get purge gnome" and it said that it did not exist. So i ran the "Remove Orphaned Packages" and that worked very well, it removed everything that i could see as gnome.

I'm calling this solved!!!
Thank you all for your help.

JoeNZ

---

