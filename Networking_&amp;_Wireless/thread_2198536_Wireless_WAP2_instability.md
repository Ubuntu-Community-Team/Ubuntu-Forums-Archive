---
title: "Wireless WAP2 instability"
date: 2014-01-09
forum: Networking &amp; Wireless
---

### Post by adriano-ulhoa on 2014-01-09
Hi guys!

I am having some problems to stablish a stable connection in a Wireless network with a WAP2 Enterprise set and PEAP, but the funny part is that I don't have the same problem with my home wireless. Does anyone know any solution to that or any specific app to control the wireless of such specific set?

---

### Post by varunendra on 2014-01-10
Welcome to Ubuntu Forums !

Please open a terminal (Ctrl-Alt-T) and check -
```
sudo cat /etc/NetworkManager/system-connections/*"<your Enterprise Network connection name>"*
```
where *[COLOR="#0000CD"]<your Enterprise Network connection name>[/COLOR]* is the name by which the connection appears in the Network Manager's drop down list (put the name in double-quotes if it contains blank spaces).

Do you see any line that says "system-ca-certs=true"? If yes that may be the problem. You should change its value to "false". The commandline way to do so is -
```
sudo sed -i '/system-ca-cert/ s/true/false/' /etc/NetworkManager/system-connections/*[COLOR="#0000CD"]<your Enterprise Network connection name>[/COLOR]*
```

However, if you don't see a line like above, or if it doesn't help, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

