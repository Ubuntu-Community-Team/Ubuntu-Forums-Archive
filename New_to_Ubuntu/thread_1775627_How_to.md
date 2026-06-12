---
title: "How to?"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by babymoon on 2011-06-05
E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-natty.list
E: The list of sources could not be read.

HOW CANI FIX IT?PLEASE

---

### Post by wildmanne39 on 2011-06-05
> **babymoon said:**
> E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-natty.list
E: The list of sources could not be read.

HOW CANI FIX IT?PLEASE
Hi, try 
```
sudo rm -r /var/lib/apt/lists
```
```
sudo apt-get update
```

---

### Post by babymoon on 2011-06-05
I already try with that code. Friend!! another code for solving it?

---

### Post by jtarin on 2011-06-05
> **babymoon said:**
> E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-natty.list
E: The list of sources could not be read.

HOW CANI FIX IT?PLEASEIn the terminal enter the command ```
gksudo gedit /etc/apt/sources.list.d
``` This will open the sources.list.d. Copy and paste it here. Use the "#" code tag in your reply to frame the response.

---

### Post by Joe of loath on 2011-06-05
> **jtarin said:**
> In the terminal enter the command ```
gksudo gedit /etc/apt/sources.list.d
``` This will open the sources.list.d. Copy and paste it here. Use the "#" code tag in your reply to frame the response.

You mean CODE]gksudo gedit /etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-natty.list[/CODE] ;)

---

### Post by jtarin on 2011-06-05
Yea! But ```
gksudo gedit /etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-natty.list
```

---

### Post by Elfy on 2011-06-05
Thread closed. Please do not post duplicates, it dilutes community effort.

---

