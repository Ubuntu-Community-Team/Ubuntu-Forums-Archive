---
title: "Network Manager Won't Work"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by rvickers on 2006-11-10
I've just installed Network Manager on a new Toshiba Satellite (edgy). Network Manager says "No network connection", System->Networking-> no connections checked, Wifi Radar shows my wireless router. /etc/network/interfaces has configuration in it and  when I try to edit out the lines, I get a "Permission denied".
](*,) 
Heeelp and thx...

---

### Post by boban on 2006-11-10
I don't know how to help you with your GUI tool, but...

> **rvickers said:**
> /etc/network/interfaces has configuration in it and  when I try to edit out the lines, I get a "Permission denied".

Are you editing as root? 

```

#substitute gedit with your favourite editor
#from terminal:
sudo gedit /etc/network/interfaces

#or from "run command" (alt+f2):
gksu gedit /etc/network/interfaces

```

---

### Post by rvickers on 2006-11-10
Thanks boban, I should'ave read some more, sudo is a common command. I've lived my life as root until ubunto. My next problem is how do I configure an Ip for my connections using Network Manager?

---

