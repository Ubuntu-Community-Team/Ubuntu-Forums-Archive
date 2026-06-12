---
title: "Establishing a Wifi connection at boot time"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by decapsuleur on 2008-03-05
Hi everyone !

I am currently setting up a server running Ubuntu 7.10 and I've been wondering how to configure Ubuntu to establish a secure wireless connection (WPA2 Personnal) automaticly without having to login. 

I can get the connection working automaticly and flawlessly as soon as I get to the desktop (after having entered my username/password) but since this computer will be sitting on a shelf without any input device or monitor and setup to boot automaticly in my absence, this scenario is quite impracticable.

I am willing to try any of your suggestions except "rm -rf *.*" ;)

Thank you very much !

Decapsuleur

---

### Post by spd106 on 2008-03-07
The default tool for managing wireless connections in Ubuntu is Network Manager. NM doesn't currently support system wide settings, it works purely on a user basis.

This means you will have to disable roaming mode and use the older tools to set up a connection. I recommend that you follow one of the sticky guides on page 1 on the network sub-forum. It's not too tricky to set-up, but it's not as easy as using NM. 

Hopefully this feature will be in NM 0.7, which will likely land in Ubuntu 8.10 (Intrepid).

---

### Post by Arthur Archnix on 2008-03-07
Just configure the interface in /etc/network/interfaces and then it will be brought up before login. If for some reason it doesn, then add a line to bring it up in /etc/rc.local ... something like ifup eth1 or whatever.

This link may be useful: [http://ubuntuforums.org/showpost.php?p=1884945&postcount=1](http://ubuntuforums.org/showpost.php?p=1884945&postcount=1)

---

