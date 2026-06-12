---
title: "NetworkManager error"
date: 2006-07-20
forum: Networking &amp; Wireless
---

### Post by sockrebel on 2006-07-20
I installed network-manager-gnome and upon reboot, I got this message:
"The NetworkManager applet could not find some required resources.  It cannot continue."
any ideas?  would appreciate any help

---

### Post by stanz on 2006-07-20
I've just come from [this page]("https://help.ubuntu.com/community/WifiDocs/NetworkManager"), which has some info ya might wanna check out.
> User comment:  If you get the error.. "The [NetworkManager]("http://packages.ubuntu.com/dapper/net/network-manager-gnome") applet could not find some required resources. It cannot continue."[LIST]
[*]  Open up a terminal & type in .. ```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/ 
```  I've only come across this error once, & this fixed it straight up [IMG]https://help.ubuntu.com/htdocs/ubuntu/img/biggrin.png[/IMG]:D[/LIST] This is towards bottom of page, but a full page read- might help ya   :mrgreen:
I'm on desktop, & found this to be like 'Network Tools', and without it working for me...I donno..  ](*,)

---

### Post by sockrebel on 2006-07-20
worked great! thanks!!!

---

### Post by stanz on 2006-07-25
Kewl! :)

---

