---
title: "How do I see what processes or programs are running on Jaunty 9.04?"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by Spacestationmax on 2010-08-10
How do I see what processes or programs are running on Jaunty 9.04?

---

### Post by kr651129 on 2010-08-10
```

$>sudo apt-get install htop
$>htop
```

---

### Post by Spacestationmax on 2010-08-10
Very helpful!

Thanks

How do I make a toolbar icon for it or place it in the applications menu or make an icon for it on my desktop?

---

### Post by kr651129 on 2010-08-10
> **Spacestationmax said:**
> Very helpful!

Thanks

How do I make a toolbar icon for it or place it in the applications menu or make an icon for it on my desktop?

right click the desktop

then you should be able to "Create a launcher"

and enter htop for the name and htop for the command and check run in terminal

---

### Post by Elmer Fudd on 2010-08-10
> **Spacestationmax said:**
> How do I see what processes or programs are running on Jaunty 9.04?

Is not System Monitor installed with 9.04?

Menu:
System/Administration/System Monitor

Click on Processes tab.

If it is not installed:

```
sudo apt-get install gnome-system-monitor
```

---

### Post by Spacestationmax on 2010-08-10
> **kr651129 said:**
> right click the desktop

then you should be able to "Create a launcher"

and enter htop for the name and htop for the command and check run in terminal

I cant find anywhere to check run in terminal???

---

### Post by Spacestationmax on 2010-08-10
> **Spacestationmax said:**
> I cant find anywhere to check run in terminal???

O I found it in the Type: drop down menu Thanks

---

