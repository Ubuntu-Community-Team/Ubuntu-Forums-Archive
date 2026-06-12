---
title: "HP nc8230 wireless (ipw2200)"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by AAM on 2007-07-06
[SIZE=3]I would be grateful for any help. I am proficient at wireless via ndiswrapper, but my work laptop is supposed to use ipw2200 with Ubuntu 'flawlessly'. Yeh, right! Mine does not, so I was looking for help to resolve my mc8230's inability to access my home wireless access point. 

I can't work out if the problem is Ubuntu's wireless config or the HP's rt_kill switch malfunctioning. The command [/SIZE]> [SIZE=3]sudo /bin/echo 0 > /sys/bus/pci/drivers/ipw2200/0000:02:04.0/rf_kill[/SIZE][SIZE=3] results in the message [/SIZE]> Permission denied[SIZE=3]. I don't understand this because either I can do this as root, or I can't, yet this guy ([http://minvelst.dyndns.org/cls_php/byn/notacion_debian/index.php?entry=entry061011-020246](http://minvelst.dyndns.org/cls_php/byn/notacion_debian/index.php?entry=entry061011-020246)) says that you can enable RF transmission with this command (actually he didn't use **sudo** but that makes no difference for me anyway!)

[/SIZE][SIZE=2][COLOR=#204a87][SIZE=3]S[/SIZE][/COLOR][/SIZE][SIZE=3]o, my first question relates to how to change the rf_kill switch. Or more to the point, how do I get my system to let me change the rf_kill.

[/SIZE][SIZE=2][COLOR=#204a87][SIZE=3]A[/SIZE][/COLOR][/SIZE][SIZE=3]nd, my second question relates to Ubuntu wireless setup. The WEP password is supposed to be put in in hexadecimal format (which seems to be of the form xxxx-xxxx-xx), but I have previously generated an ASCII string key which my access point is waiting for but which is much longer than the hexadecimal string length. So how do I present the access point with a WEP key which is in a hexadecimal format but which will match the ASCII one it has?[/SIZE]

---

