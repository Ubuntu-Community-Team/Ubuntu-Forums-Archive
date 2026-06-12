---
title: "ubuntu 10.10 or ubuntu server ?"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by naved ..... on 2011-04-19
if i want to practice a lot of programming (server side ) like python , perl , php, css,mysql etc 

and also c, c++,java and advance java then which os will suite my requirement wheather ubuntu 10.10 or ubuntu server ..help me plz ...dont provide me unnecessary links plz ....
i need a short & sweet answer ...

---

### Post by Locke_99GS on 2011-04-19
A Linux server is just a Linux installation with server softwares running on it.
A Linux desktop is just a Linux installation with desktop softwares running on it.

A typical server install will NOT include any desktop or other graphical stuffs.
A typical desktop install will NOT include any server softwares on it.

You CAN run server softwares on a desktop install.
You CAN run desktop softwares on a server install.


IMO, though, you will probably be happiest with a graphical environment to work in while programming. You may want to install *apache2, php5, mysql-server, build-essential* and your ID of choice on top of your Desktop installation.

---

### Post by naved ..... on 2011-04-19
so server will suite me ( is that u r saying ) and the softwares like php, apache 2, mysql , perl will be preloaded in my server os .?

---

### Post by Locke_99GS on 2011-04-19
I was actually recommending the regular desktop install with the server softwares you need installed. :) It doesn't really matter either way. 

When/if you install the server, you'll be presented with a list of things you can have it optionally install for you, including the LAMP stack.

Be aware that out-of-box, server editions have NO graphical interface. Command-line only.

---

### Post by daweefolk on 2011-04-19
The server install will only have the command line by default. The desktop install will include a gui and terminal emulators. You can install a gui on the server install with apt-get though. Just a couple extra steps if you want to go with server.

---

