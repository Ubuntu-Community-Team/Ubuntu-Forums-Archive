---
title: "Xp Ubuntu home networking/fileserving problem..."
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by dokumentamarble on 2006-08-12
i am trying to network my ubuntu machine to act as a fileserver on my home network, i can ping ubuntu from xp but it doesnt show up on the networking tables. I would like to map a network drive to the ubuntu machine but have to find it first. (I have the GUI ubuntu installed not the server.)

---

### Post by gerbman on 2006-08-13
[This]("http://ubuntuforums.org/showpost.php?p=1265314&postcount=2") is how I have my fileserver set up. After doing that, you should be able to map the shared folder/drive in Windows under "My Computer -> Tools -> Map Network Drive". You can use something like the following for the location of the share:```
\\192.168.0.10\sharename
```Substituting the appropriate IP address and share name.

---

