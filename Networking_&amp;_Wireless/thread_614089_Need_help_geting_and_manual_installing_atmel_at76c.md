---
title: "Need help geting and manual installing atmel at76c503a-source driver"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by UnBr34KaBl3 on 2007-11-15
I need to install it manualy becouse synaptic doesn't work (no internet connection). Please help me get the right one for Gutsy Gibbon. I think that i maybe have it, but I dont know how  to install it. It was something about:

make

make install

dont mean a **** to me:confused:

I'm used to windows but just loves ubuntu exept that this just dont want to work:(

[http://img155.imageshack.us/img155/9459/screenshot2xm1.png](http://img155.imageshack.us/img155/9459/screenshot2xm1.png)
As you can see it says it is conected but it isn't:mad:

---

### Post by chaffeur on 2007-11-15
open a terminal (Alt+F2) and go to the directory where you have the source code (use cd *directoryname* to change directory) then type.
When your in the right directory try typing ./configure to see if there is any packages that you miss to compile the source code. If there is you'll have to download them or get them in any other way, which might be a problem if you don't have a internet connection.
If all goes well you type *make* to compile the source code. If all goes well after that you type *sudo make install* to install the driver.

---

### Post by UnBr34KaBl3 on 2007-11-16
Thank you. I can now surf with Firefox but the synaptic installer doesn't work...

---

### Post by chaffeur on 2007-11-17
Try a different server in synaptic, maybe the server you've selected is off line or something.
I'm not using synaptic myself, so I don't really know how to do that but have a check under settings or something. Otherwise you can do it  manually through the terminal:
> 
cd /etc/apt/
sudo gedit sources.list


do have a look at [the Ubuntu Wiki page about repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu").
Here's a bit info about editing it manually too : [https://help.ubuntu.com/community/Repositories/CommandLine]("https://help.ubuntu.com/community/Repositories/CommandLine").

---

