---
title: "Wireless not starting after reboot"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by johnstanton on 2007-01-06
Hello, 

I got my wireless up and running on my laptop but everytime i reboot i need to run sudo /etc/init.d/networking restart

Once I do that wireless connects, Is there away to make this happen on boot, I am using wpa2 so i configured all the setting in /etc/network/interface,

Any help would be great. 

Thanks

John Stanton

---

### Post by teaker1s on 2007-01-06
if it's ndiswrapper  by 
[COLOR="Red"]sudo gedit /etc/modules[/COLOR]
then put the word **ndiswrapper**

save file

gnome
[COLOR="Red"]network-manager-gnome[/COLOR]
this makes switching networks less painful

---

