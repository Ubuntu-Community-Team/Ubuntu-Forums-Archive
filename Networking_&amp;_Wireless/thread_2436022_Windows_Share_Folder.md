---
title: "Windows Share Folder"
date: 2020-01-30
forum: Networking &amp; Wireless
---

### Post by a.mushtaqali on 2020-01-30
Hello!
i'm new to Ubuntu, Linux. On windows i run Run Command on windows 10 to access Media Server provided by my ISP. like this (Windows key+R) IP Address \\192.168. but i'm unable to do this in Ubuntu. Currently i'm running Ubuntu 19.10
Sorry for my bad English language.

---

### Post by CelticWarrior on 2020-01-30
Open the file manager and at the bottom right type smb://IP_ADDRESS (replace with the IP address you've been using). When open you can pin it so next time all you need to do is click on it.

---

### Post by Morbius1 on 2020-01-30
If you are looking for the Linux equivalent of Run ( Windows Key + R ) it's [highlight]Alt + F2[/highlight]

The only problem is that in Windows when you run \\192.168.0.100 it assumes you are asking for the SMB host at that address and it automatically opens explorer to that address. In Linux you have to tell it explicitly what to do:

Alt + F2
then
```
nautilus smb://192.168.0.100
```

---

### Post by CelticWarrior on 2020-01-30
> **Morbius1 said:**
> 
Alt + F2
then
```
nautilus smb://192.168.0.100
```

This ^^^^worls too. Of course, replace the IP address with the one that is your Windows share.

And it's really surprising, at least to me, that you asked the exact same thing almost a year ago - [https://ubuntuforums.org/showthread.php?t=2411619](https://ubuntuforums.org/showthread.php?t=2411619) -, didn't gave any feedback to the person trying to help you, and learned nothing meanwhile. Definitely not the way to go, personal opinion.

---

