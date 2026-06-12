---
title: "server os alongside windows?"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by naved ..... on 2011-04-30
can i instal ubuntu server alongside windows 7 or it should the only os on my machine , i m installing server os coz i need to run a website from my system !
and from where i can learn some good cli for operating server o.s bcoz i dont know how to operate on cli i m a windows user so facing this problem but i ll ready to learn the stuff...

---

### Post by kaldor on 2011-04-30
Dual booting would be a huge disaster if you want to host. If you have enough RAM, why not use VirtualBox on Windows? You can install a "guest" OS on a virtual partition which has no effect on the rest of your system. You can then set it up to work as a virtual server.

---

### Post by naved ..... on 2011-04-30
can i use live cd option to test ubuntu server like desktop edition ? and from where to learn cli for srever edition ?

---

### Post by kaldor on 2011-04-30
Step 1: Install the latest [VirtualBox for Windows here]("http://www.virtualbox.org/wiki/Downloads")

Step 2: Get a Linux .iso of your choice. Since you mentioned CLI Ubuntu, [here is a link to Ubuntu Server]("http://www.ubuntu.com/download/server/download") which is CLI only (options exist to install GUI).

Step 3: Once the Ubuntu .iso is finished, you can set up Virtualbox to host Ubuntu. [Here]("https://help.ubuntu.com/community/VirtualBox/FirstVM") is a guide. Outdated pictures and it's on Ubuntu, but it should work near identically on Virtualbox for Windows.


Note that using Virtualbox is pretty much a fool-proof way to try an OS, since you can't interact with or damage your real hard drive. Also, to learn how to use the CLI, get used to using it. Try using the CLI as much as possible instead of the GUI, and eventually you'll catch on.

---

### Post by kaldor on 2011-04-30
Double post, but oh well :)

Just on a side note, the company behind Ubuntu (Canonical) offers a 55-minute trial of their Services on Ubuntu. You can create an account and sign in to use Ubuntu Server remotely with their technologies for an hour.

---

