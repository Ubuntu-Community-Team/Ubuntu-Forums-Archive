---
title: "permissions"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by som1special2 on 2009-08-29
I had a problem with grub, (error 21) and have decided to move to another hard disk and reinstall Linux Mint. I wanted to remove some of my thunderbird files and firefox files from the affected disk, but I cannot access them as i do not have the permissions. I have tried right clicking and opening as root with not success. any help is appreciated!

---

### Post by NoaHall on 2009-08-29
sudo nautilus 
And then try. What are you trying to access them from?

---

### Post by stinger30au on 2009-08-29
chown and chmod are the tools you need to run i believe

---

### Post by credobyte on 2009-08-29
```
gksudo nautilus &

```

---

### Post by som1special2 on 2009-08-29
I will be trying to access the files from an external disk

---

### Post by NoaHall on 2009-08-29
then yes, you need to use chown and it as your own drive.

For example, I would do 

```

chown noah /media/disk

```

---

