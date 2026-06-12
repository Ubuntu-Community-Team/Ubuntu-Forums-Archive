---
title: "I love this OS! but I dont love firestarter"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by Mickeysofine1972 on 2006-08-03
Hi

PLease can any Kubuntu 6.06 LTS users give me some advice on running firestarter on boot time?

I tried to create a fiel called <homedir>/.kde/Autostart/firestarter with the following lines in it:

```

#!/bin/sh
sudo firestarter --start-hidden

``` 

NB: I have already setup my user as a sudoer so this should be fine.

this seems OK but doesnt start when I reboot!?!?!?!

any pointers would be geatly welcomed ... except C pointers, (warning geeky programming joke just happened!).

Mike

---

### Post by jpkotta on 2006-08-03
You should use the init script:```
sudo /etc/init.d/firestarter start
```  

To get it to start automatically, make a symlink in /etc/rc2.d.

```
sudo ln -s /etc/init.d/firestarter /etc/rc2.d/S99firestarter
```

---

