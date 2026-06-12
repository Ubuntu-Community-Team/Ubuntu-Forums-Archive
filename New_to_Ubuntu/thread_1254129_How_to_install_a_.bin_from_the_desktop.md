---
title: "How to install a .bin from the desktop"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by cranecreek on 2009-08-31
Not new to linux but the desktop is. How do you install a .bin from the desktop. Just got a new dell with 8.1 Intrepid and I'm clueless. Always done it in the terrminal. A little help please.


Thanks

---

### Post by ibuclaw on 2009-08-31
[LIST=1]
[*]Right-click file, select "**Properties**"
[*]Select the "**Permissions**" tab
[*]Check the "**Allow executing file as program**" box, then Close.
[*]Double-click file
[*]Select "**Run in Terminal**" if it's a CLI .bin installer
or Select "**Run**" if it's a GUI .bin installer
[/LIST]

Regards
Iain

---

### Post by colau on 2009-08-31
> **cranecreek said:**
> Not new to linux but the desktop is. How do you install a .bin from the desktop. Just got a new dell with 8.1 Intrepid and I'm clueless. Always done it in the terrminal. A little help please.


Thanks
Or
```

chmod +x file.bin
./file.bin

```

---

### Post by drhuid on 2009-08-31
Sorry but neither of the above work. After changing to executable I get a failure note "no application is known for this type of file".

---

### Post by cranecreek on 2009-08-31
I wasn't patient so I used the terminal

```
chmod a+x file.bin
./file.bin
```Thanks for the destop answer will try that next time.

---

