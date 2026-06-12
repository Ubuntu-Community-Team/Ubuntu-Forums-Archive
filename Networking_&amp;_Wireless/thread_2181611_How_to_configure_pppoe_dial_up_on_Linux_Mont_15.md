---
title: "How to configure pppoe dial up on Linux Mont 15?"
date: 2013-10-18
forum: Networking &amp; Wireless
---

### Post by Mir_Ferdous on 2013-10-18
[COLOR=#070F14][FONT=Verdana]I have to dial up with user name and password in broadband connection.But I can not find any option in Linux Mint 15 (cinnamon).[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]How to dial up over PPPoe on it?[/FONT][/COLOR]

---

### Post by praseodym on 2013-10-18
Hi,

is the Network-Manager installed? If yes, start it from terminal with
```

gksudo nm-connection-editor
```
Use the section "DSL"

---

