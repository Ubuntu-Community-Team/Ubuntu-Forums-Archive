---
title: "installing .run problem"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by ave2 on 2010-10-29
I just downloaded the latest ATI drivers- a .run file

so I go into terminal and type in sudo /home/user/ati.run

the "/home/user/ati.run" part was just the file dragged onto the terminal.

in the past that worked for me, this time it says command not found.

any ideas what I can do

---

### Post by oldos2er on 2010-10-29
Is ati.run executable? ```
chmod a+x ati.run
```

---

### Post by kaldor on 2010-10-29
> **ave2 said:**
> I just downloaded the latest ATI drivers- a .run file

so I go into terminal and type in sudo /home/user/ati.run

the "/home/user/ati.run" part was just the file dragged onto the terminal.

in the past that worked for me, this time it says command not found.

any ideas what I can do

```
cd /home/yourusername
chmod a+x ati.run
sudo ./ati.run
```

Above is the general stuff for this. I believe though, do you have to exit X if you want to install drivers.

---

### Post by ave2 on 2010-10-29
> **kaldor said:**
> ```
cd /home/yourusername
chmod a+x ati.run
sudo ./ati.run
```

Above is the general stuff for this. I believe though, do you have to exit X if you want to install drivers.

you genius!!

---

