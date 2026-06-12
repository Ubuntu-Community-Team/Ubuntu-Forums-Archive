---
title: "automatic module loading"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by xodeus on 2008-03-02
HI there.
Now I have a final question.
I've built my own module (rt2860sta.ko)
Now it's located in my home directory and I'm manually loading it with ```
sudo /sbin/insmod rt2860sta.ko
``` and it's working...

But i want to automaticly load it at boot.
How do I do that?

Thank you

---

### Post by SpaceTeddy on 2008-03-02
open /etc/modules and just put the module name in there. that file is for loading special modules at boot time

---

### Post by xodeus on 2008-03-03
I'm not at home right now, but I still have i little question before that. Because when i type sudo modprobe rt2860sta, then my michine can't find the module. Do I have to copy the ko file to a specific directory?

---

### Post by SpaceTeddy on 2008-03-03
i have not really installed modules myself, but yes, fpr the file to find it it must be in the appropriate folder... usually, in addition to the make there is a make install which copies it into the right module folder...

another possibility that you can do it put the full command in your /etc/rc.local file, which is run every time you boo aswell - but it is intended for command/scripts to be started at boot time, and not for modules. if you cannot get the right folder, try load it as a command (like in your first post) instead :)

---

### Post by xodeus on 2008-03-03
I did the make install and the module loads automaticly now. Funny that this isn't described in the readme file...
But thanks anyway...
Now I only want the wicd tray to start automaticly but it wont...

---

