---
title: "Static IP help"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by Max Foreman on 2007-10-13
I just finished installing Ubuntu server edition.  I installed the LAMP package and everything went smoothly.  

Here is my problem.

From the command line I type "Sudo vi /etc/network/interfaces" this brings up the configuration file I need but when I try to edit it makes these loud beeps at me.  BEEP BEEP BEEP every time I try to type something in.  :mad:

Honestly I'm not even sure how to edit this file.  I know the information to put in but i don't know how to put it in.  I don't know if there is something wrong or that It's just because I'm a noob. 

I've also read it's a good idea to back this file up before you edit it, but I have know idea how.

---

### Post by milosz.galazka on 2007-10-13
Try to use pico, nano, ...
There are couple of editors available after system installation.

Before using vi you need to read [tutorials]("http://www.google.com/search?q=vi+tutorial&btnG=Szukaj+w+Google&lr=")

To backup try
```
cd /etc/network/
cp interfaces interfaces.bak
```

And if you want to revert changes you made
```
cp interfaces.bak  interfaces
```

You can see differences by using command
```
diff interfaces interfaces.bak 
```

---

### Post by Max Foreman on 2007-10-13
Thanks :)

---

