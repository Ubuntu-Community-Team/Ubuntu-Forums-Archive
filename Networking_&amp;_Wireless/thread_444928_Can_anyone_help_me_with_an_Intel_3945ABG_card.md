---
title: "Can anyone help me with an Intel 3945ABG card?"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by Oneironaut on 2007-05-15
well, I just installed Feisty , the problem is  that even though my network-manager finds networks and everything, it even asks for the wep key, it never connects.

I found several pages regarding this subject, but I´m a total newbie in Linux so I couldn´t get anything working, can anyone help me? or point me to some place.


thanks a lot

---

### Post by QuartersMostly on 2007-05-15
Are you trying to use WEP? Does it work if you don't use WEP? I haven't tried this solution yet, but I posted a similar thread which might help you: [http://ubuntuforums.org/showthread.php?t=444009](http://ubuntuforums.org/showthread.php?t=444009) .

---

### Post by Oneironaut on 2007-05-15
Running the following code through terminal worked:

```

sudo iwconfig eth1 essid burrito
sudo iwconfig eth1 key 0123456789abcdef
sudo dhclient eth1
```

with a wep key, using an intel 3945ABG wireless card.

Although I guess this means that there´s  no way to monitor the connection right?

does anyone know how to terminate the connection, and what to do if it&#347; an open network?

---

