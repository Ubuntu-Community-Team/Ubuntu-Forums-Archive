---
title: "Problem after removing GNOME 3 in 11.04"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by gokul_beece on 2011-04-29
Hi , 

I installed gnome 3 in 11.04 ubuntu. i cant able to login using "ubuntu classic" mode. 
So I uninstalled the gnome 3 using the follwing command
sudo apt-get install ppa-purge
sudo ppa-purge ppa:gnome3-team/gnome3

but after reboot i am not able to load x server. its working CLI prompt

How can i revert back old configuration ?

Goks

---

### Post by Calash on 2011-04-29
I think if you type the following it should reinstall anything that is missing


```

sudo apt-get install ubuntu-desktop

```

---

