---
title: "windows network problem"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by yf1208 on 2007-08-16
I have two machines connected via a router,one is using ubuntu another windows xp.

The problems with the ubuntu is after installing Samba following instructions from this site

[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

the windows computer in the network place just disappeared,yesterday before i install samba i could still see it there,i could even edit some of the files there.


The problem with the windows machine is,it can't detect the folders that are being shared in ubuntu(the settings in the Shared Folders part is correct,i already selecter shared through windows network SMB).
The windows machine could detect the Linux computer over the network thou

---

### Post by yf1208 on 2007-08-16
bump..help pls

---

### Post by callan79 on 2007-08-16
> **yf1208 said:**
> The problem with the windows machine is,it can't detect the folders that are being shared in ubuntu(the settings in the Shared Folders part is correct,i already selecter shared through windows network SMB).The windows machine could detect the Linux computer over the network thou

Hi there,

I've found that the whole 'browse network' thing is a little dodgy, in Ubuntu and in Windows. What happens if you just try to access the other computer via IP Address? This should show you all the shares on that computer.

In Ubuntu, go to places >> computer, and then in the address bar :  smb://x.x.x.x, where x.x.x.x is the IP address of your Windows machine.

In Windows, go to start >> my computer, and in the address bar :  \\x.x.x.x, where x.x.x.x is the IP address of your Ubuntu machine.

Any joy?

Cheers
Callan

---

