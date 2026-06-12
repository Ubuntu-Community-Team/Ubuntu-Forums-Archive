---
title: "Cant Static IP"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by some11 on 2007-06-05
Hey!
First day with Ubuntu - please be nice!
Right
I'm behind a router, and I need static IP, for the web server...
I'm connecting wireless... (WLAN0 & WMASTER0)

When I do manual configuration,and type in all the details 
(WEP 64BIT HEX // SHARED // 192.168.0.3 //255.255.255.0 //192.168.0.1//SSID)
It doesn't connect, cant even ping myself (192.168.0.3) 

Auto do, I either get "keyring" and or "please type in your WEP key"..then I can connect! (via DCHP). then its fine! Im on the net :)

I also cant right click on network thingy , in the top right,  and goto "connection information", I get the following error
"Could not find some required resources (the glade file)

edit: Tried this, Disabling IP v6, ([http://ubuntuforums.org/archive/index.php/t-6841.html](http://ubuntuforums.org/archive/index.php/t-6841.html))

Sorry, if this doesnt make any sense, im getting stressed out about this!

---

### Post by some11 on 2007-06-06
WOOOOO!!!!
CRACKED IT! (now I can go and sleep!)

if it helps anyone.... "Shared, 64bit HEX WEP, Key index 2,  static IP"

sudo nana /etc/network/interfaces

auto wlan0
iface wlan0 inet static
wireless-essid The_Box
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1
mode Managed
wireless-key [2] 69xxxxxxD


Edit:
This help me out
[http://www.rvdavid.com/blog/how-i-got-my-belkin-f5d6001-wireless-card-running-on-feisty-fawn/](http://www.rvdavid.com/blog/how-i-got-my-belkin-f5d6001-wireless-card-running-on-feisty-fawn/)

---

### Post by rvdavid on 2007-11-14
> **some11 said:**
> WOOOOO!!!!
CRACKED IT! (now I can go and sleep!)
...

This help me out
[http://www.rvdavid.com/blog/how-i-got-my-belkin-f5d6001-wireless-card-running-on-feisty-fawn/](http://www.rvdavid.com/blog/how-i-got-my-belkin-f5d6001-wireless-card-running-on-feisty-fawn/)


Please use rvdavid.net instead... I had to get a new domain name due to my former webhost 2mhost holding my old domain name hostage and not replying to any of my emails. :( 

[http://blog.rvdavid.net/how-i-got-my-belkin-f5d6001-wireless-card-running-on-feisty-fawn/](http://blog.rvdavid.net/how-i-got-my-belkin-f5d6001-wireless-card-running-on-feisty-fawn/)

regards,

---

