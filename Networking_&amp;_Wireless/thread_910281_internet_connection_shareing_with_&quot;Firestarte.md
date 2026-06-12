---
title: "internet connection shareing with &quot;Firestarter&quot; problem"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by Ahmed Alaa on 2008-09-04
hello

when i try to run the firestarter i get this problem
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=84034&stc=1&d=1220540378[/IMG]
[IMG]http://http://ubuntuforums.org/attachment.php?attachmentid=84035&stc=1&d=1220540378[/IMG] [IMG]http://ubuntuforums.org/attachment.php?attachmentid=84035&stc=1&d=1220540378[/IMG]

i use wireless connection for internet and LAN to share connection withe other windows pc

wifi0 is the wireless card and the eth0 is the LAN card ?? 
and what is the ath0 ??

how can i solve this problem ?? 

thanks 
Ahmed Alaa:)

---

### Post by tuxxy on 2008-09-04
You should try ufw as firestarter is discontinued I beleive, type in terminal

```
ufw
```

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

---

### Post by Ahmed Alaa on 2008-09-04
i enable it and its the same 

when i type > sudo ufw status
i only get > ~$ sudo ufw status
Firewall loaded 

i think it may be something with the driver coz the wireless work automaticly i dont use any drivers??

and is there any other graphical sofrware for shareing the connection by LAN withe one windows pc ??

---

### Post by jimv on 2008-09-04
Go into the Firestarter settings and make sure that you have the correct network connections set for LAN and Internet.

---

### Post by Ahmed Alaa on 2008-09-04
i allready do that 

i set (wifi0) as the internet and (eth0) as the local 

i get the internet via wireless "D-link DWA-520" and the LAN is build in the motherbord 

but i dont know what is the (ath0) ??

thanks

---

