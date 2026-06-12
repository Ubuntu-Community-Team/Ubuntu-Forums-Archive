---
title: "I dont' know how to start a program I installed"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by zulubanshee on 2010-10-12
I  installed VMWare,, but now I don't know where to find it or how to boot it. 

Any help would be greatly appreciated.

---

### Post by ft-Orchard on 2010-10-12
> **zulubanshee said:**
> I  installed VMWare,, but now I don't know where to find it or how to boot it. 

Any help would be greatly appreciated.

To start it: (in terminal)
```

vmplayer (for vmware player)

vmware (for workstation)

```

You should create links in your menu. 
Go to: "preferences > main menu"

---

### Post by zulubanshee on 2010-10-12
I tried that: this is what i get"

/usr/bin/vmware: 166: cannot open /etc/vmware/locations: No such file
exec: 180: /lib/wrapper-gtk24.sh: not found

---

### Post by spillage2 on 2010-10-12
should be under system tools. have you tried virtual box instead i find it much better.

---

### Post by zulubanshee on 2010-10-12
all i have is Sys Info under system tools.

---

### Post by zulubanshee on 2010-10-12
Maybe a good start would be if someone could tell me how to find which folder it's in. I clicked on the .deb file and it installed but I don't know where. Is there a default?

---

### Post by yanes on 2010-10-12
Why don't ask your linux ?
In a console session type :> whereis vmware
the answer is directory path 
go into it and  look for an executable 

Not i never used vmware but this a solution for "[B]: I dont' know how to start a program I installed"
Good luck
[/B]

---

### Post by GabrielYYZ on 2010-10-12
remember the terminal is case-sensitive, so this:

> **ft-Orchard said:**
> To start it: (in terminal)
```

vmplayer (for vmware player)

vmware (for workstation)

```You should create links in your menu. 
Go to: "preferences > main menu"

might be:

```

VMPlayer (for player)

VMWare (for workstation)

```worth a try, if you're still having problems with it.

---

### Post by zulubanshee on 2010-10-12
ok looking better. I found a file, but it appears to be not working for me. I found /usr/bin/vmware, but I get this message. 

/usr/bin/vmware: 166: cannot open /etc/vmware/locations: No such file
exec: 180: /lib/wrapper-gtk24.sh: not found

Is there something I should be looking for? 
Is the /usr/bin directory the one where .deb programs are put in by default?

---

### Post by zulubanshee on 2010-10-12
Also, I tried to add the program to the menu, but when I went to Preferences > Main Menu, I see it is not in the list of programs to be added. So now I'm wondering if I've done something wrong.

---

