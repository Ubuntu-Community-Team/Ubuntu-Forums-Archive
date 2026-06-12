---
title: "Lost my network connections manager!"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by rosstheboss on 2009-03-03
Hi all,

I changed my taskbars, and ended up deleting the default taskbar and creating a new one and adding on the applets I normally use. However, I cannot find how to add the network connections manager back into the taskbar; I can see a network monitor applet, but not the manager. After referring to the documentation I read that I could at least access the manager through System > Administration > Network. Irritatingly, all I have on that menu is 'network tools', which only offers tools like ping, port scan etc. I'm sure the answer is obvious, but it's a very frustrating problem.

While I'm at it, I'll ask how you add back the default shut down menu to the taskbar along with the network connections manager. Currently I must access the shut down menu through the main menu.

Thanks,
Ross

---

### Post by x33a on 2009-03-03
try system -> preferences -> network configuration.

check if the network manager is added to startup:

system -> preferences -> sessions.

to add shutdown to the panel

right click -> add to panel -> user switcher.

---

### Post by rosstheboss on 2009-03-03
System > Preferences > Network configuration brings up a window called network connections, but on the wireless tab it simply lists previous connections I've made. Is there a way to get it to display all the connections available?

The notifications area was the applet I should have installed, now it works properly. I'm still curious about the above though.

---

### Post by x33a on 2009-03-03
i don't use network manager, so i am not really sure.

if you want to see all the available networks(wireless), you can type
```
iwlist scan
``` in a terminal.

---

