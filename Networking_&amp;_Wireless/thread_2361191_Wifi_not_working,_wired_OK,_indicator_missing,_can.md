---
title: "Wifi not working, wired OK, indicator missing, cannot start network manager"
date: 2017-05-13
forum: Networking &amp; Wireless
---

### Post by fyfe54 on 2017-05-13
After a recent update, all networking simply stopped working.  It was probably an update, but didn't appear until after a reboot.  I have managed to get the wired side working, but despite seriously questioning my friend (Google) I have not found a solution to the wifi side.

I have attached the output from the wifi info script.  Any help would be greatly appreciated.

Thanks.

Edit:  I was having issues with PIA hanging and not connecting at about this time and was poking around some settings,. Didn't think I actually changed anything.

---

### Post by wildmanne39 on 2017-05-13
You are running 17.04 was wifi working correctly with this version or did it break when you upgraded to this version?

Please do:
```
sudo apt install --reinstall network-manager-gnome
```
Does network manager come back with the icon and does wifi work?
Thanks

---

### Post by fyfe54 on 2017-05-13
Wifi was fine after the move to 17.04.  The trouble was with PIA vpn hanging and not connecting.

ASs suggested, I ran sudo apt install --reinstall network-manager-gnome.  I rebooted, but still no wifi or icon. 

Thanks

---

### Post by wildmanne39 on 2017-05-13
I believe this will get you going:
[https://ubuntuforums.org/showthread.php?t=2361125&page=2&p=13644867#post13644867](https://ubuntuforums.org/showthread.php?t=2361125&page=2&p=13644867#post13644867)

Post 13.

---

### Post by fyfe54 on 2017-05-15
Sorry for not getting back here sooner.  Mothers' Day, work, sleep got in the way.  
I tried the solution above, but it did not work for me.   
Looking back in the terminal commands, I ran:
sudo apt remove --purge network-manager (gave broken package error)
sudo apt-get install network-manager
sudo apt-get install network-manager-gnome 
sudo apt-get install network-manager-openconnect-gnome network-manager-openvpn-gnome
sudo reboot

And I have wifi.  

I'll mark this "solved", as I have wifi back, but am not confident that it will work for anybody else.

---

### Post by wildmanne39 on 2017-05-16
I am glad it is working again.

---

