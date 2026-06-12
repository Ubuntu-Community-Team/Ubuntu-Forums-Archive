---
title: "No Wirless On Boot"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by #Reistlehr- on 2007-07-04
Ok, so i have an HP, and a beautiful, easy to install broadcom chip, ;). It;s installed and works fine. BUT, everytime i boot, it is not loaded. I have to manually go into the term and type 

```
sudo depmod -a
```
and
```
sudo modprobe ndiswrapper
```

i added ndiswrapper to the /etc/modules to see if it would do it, and nope same thing. i tried a startup script, but when i use it, it will not configure the script.

When i first start up, it only show's the wirednetwork. ifconfig shows no wlan0, and only my eth0 and lo. so it's something i've searched for on the forums, but had no luck.

any help would be greatly appreciated.

---

### Post by #Reistlehr- on 2007-07-04
And another question, why does NAIM keep sending a blank IM to myself every minute on the dot? lol. i gogoled, but no luck.

---

### Post by Ayuthia on 2007-07-04
Do you have
alias wlan0 ndiswrapper
in /etc/modprobe.d/ndiswrapper?

---

### Post by #Reistlehr- on 2007-07-04
yes i do.

---

