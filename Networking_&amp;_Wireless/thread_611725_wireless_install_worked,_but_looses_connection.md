---
title: "wireless install worked, but looses connection"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by Bart Ellebaut on 2007-11-13
Hey, 

I finally was able to install the drivers for my linksys WPC54G. For this I used ndisgtk.
Is says: hardware... , so  I configured everything, WEPkey hexadecimal,  ...
Now everytime I try to connect, after 2 seconds of connected, it's lost again.
I check out the config, and my Key is gone, the other time it has returned to ASCII.
What should I do?

btw, the configuration was also done with ndisgtk, not terminal
and I have tried the config with system==>network

I do still have my LAN ,but I have also tried it when it was disconnected, and this didn't work either.

thx
Bart

---

### Post by reckless2k2 on 2007-11-13
make sure to disable the wired interface in network manager or it will flip back and forth. so only the wireless interface should be enabled. 

might be your issue. it was mine.

---

### Post by Bart Ellebaut on 2007-11-13
I have already deplugged my cable, that didn't work,
the I enabled my wired connection. When I tried to connect wireless, he lost it and my wired connect turned back on automatically.
so I don't know if I have enabled it correctly

---

### Post by reckless2k2 on 2007-11-13
maybe i should be more clear. unplug the wired connection. then go into the wired connection in the network manager and disable it completely. you shouldn't have to reboot but go ahead and do it then. 

make sure your signal strength is good to the access point as well.

---

### Post by Bart Ellebaut on 2007-11-14
OK, 
I have done this, but still no luck, he keeps on turning my wireless down and switching my wired connection on.

---

### Post by reckless2k2 on 2007-11-14
last thing then is to comment out the eth0 lines in your interfaces config file so it'll only "see" the wireless device. 

you familiar with how to do that or need some hand holding?

---

