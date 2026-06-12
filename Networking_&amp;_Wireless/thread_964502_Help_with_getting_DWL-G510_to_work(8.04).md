---
title: "Help with getting DWL-G510 to work(8.04)"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by Snyper64 on 2008-10-31
I need help with removing the default driver in Ubuntu. I followed [THIS LINK]("https://help.ubuntu.com/community/WifiDocs/DWL-G510") but when I get to the part where I remove the Ubuntu driver I get the following error:
```
snyper64@snyper64-desktop:~$ sudo rm /lib/modules/2.6.15-26-386/kernel/drivers/net/wireless/mrv8k/mrv8k.ko
[sudo] password for snyper64: 
rm: cannot remove `/lib/modules/2.6.15-26-386/kernel/drivers/net/wireless/mrv8k/mrv8k.ko': No such file or directory
```
Is there a new module out now or am I missing something?

---

### Post by Snyper64 on 2008-11-01
bump

---

### Post by Snyper64 on 2008-11-03
bump

---

### Post by Snyper64 on 2008-11-06
Anybody? It would be nice to stop using the libraries internet and use my own again.

---

### Post by DCFC79 on 2008-11-11
> **Snyper64 said:**
> I need help with removing the default driver in Ubuntu. I followed [THIS LINK]("https://help.ubuntu.com/community/WifiDocs/DWL-G510") but when I get to the part where I remove the Ubuntu driver I get the following error:
```
snyper64@snyper64-desktop:~$ sudo rm /lib/modules/2.6.15-26-386/kernel/drivers/net/wireless/mrv8k/mrv8k.ko
[sudo] password for snyper64: 
rm: cannot remove `/lib/modules/2.6.15-26-386/kernel/drivers/net/wireless/mrv8k/mrv8k.ko': No such file or directory
```
Is there a new module out now or am I missing something?

did you install dwl g510 ok, im just asking as i tried to install it today but i couldnt find drivers unless i miassed something

---

### Post by Snyper64 on 2008-11-12
I followed the instructions exactly so they are installed as ndiswrapper sees my card. Its when I get to the part where I have to remove the Ubuntu default drivers that I end up having problems.

---

### Post by DCFC79 on 2008-11-13
> **Snyper64 said:**
> I followed the instructions exactly so they are installed as ndiswrapper sees my card. Its when I get to the part where I have to remove the Ubuntu default drivers that I end up having problems.

were the divers on the cd you got with the device or did you get them off the internet

---

### Post by Snyper64 on 2008-11-13
The Internet, I followed the instructions to a T on the link on the first post.

---

