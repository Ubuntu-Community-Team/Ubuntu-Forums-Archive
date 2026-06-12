---
title: "cannot connect to new home wifi"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by japes_c20 on 2007-11-14
I just installed ubuntu 7.04, my wifi works at public places but we just got dsl at home with a Linksys Wireless-G router and it wont connect. It recognizes the wifi but when i type in the encryption key, it wont do anything. We are using WPA-Personal security.   
Please Help.

---

### Post by scrooge_74 on 2007-11-14
do you have [wpasupplicant]("http://hostap.epitest.fi/wpa_supplicant/") installed?

from a terminal sudo apt-get install wpasupplicant

---

### Post by japes_c20 on 2007-11-14
After i type in the command in the terminal it says:
E: dpkg was interrupted, you must manually run 'dpkg - -configure -a' to correct the problem.

---

### Post by scrooge_74 on 2007-11-14
something happend like pressing CTRL + C

do a sudo dpkg--reconfigure -a to fix it

---

### Post by Apocalipssyss on 2007-11-14
I have the exact same hardware but using ubuntu 7.10, i've tried to install that package but it says that it's allready installed, any suggestion?

---

