---
title: "[SOLVED] Turning off automatic login"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-01-04
So when I installed Ubuntu on my new laptop I checked auto login but I decided I don't really like it... how can I change this? I was poking through my settings but can't find it.

~Jeff

---

### Post by howefield on 2009-01-04
Open a terminal and type

```
sudo /usr/sbin/gdmsetup
```

You'll find the option in there.

---

### Post by Rucas on 2009-01-04
Hey Jeff
Im on Ubuntu 8.04, but i do believe it's still located in the same place.
Go to SYSTEM>ADMINISTRATION>LOGIN WINDOW
Here under the SECURITY TAB you should see a checkbox **Enable Automatic Login**, just unselect it.
Cheers and Happy new year...

---

### Post by rolnics on 2009-01-04
Goto System -> Administration -> Login Window. And then click the Security tab.

---

### Post by beastrace91 on 2009-01-04
@Howe thanks for the terminal command.

~Jeff

---

