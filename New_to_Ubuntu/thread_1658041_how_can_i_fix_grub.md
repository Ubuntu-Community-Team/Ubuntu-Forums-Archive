---
title: "how can i fix grub"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by slixz85 on 2011-01-02
my bootloader will not show ubuntu after installing unity linux, could someone please walk me through fixing this. thanks to any help

---

### Post by karthick87 on 2011-01-02
```
sudo update-grub
```

---

### Post by slixz85 on 2011-01-02
> **karthick87 said:**
> ```
sudo update-grub
```

command not found. need help to fix using unity

im using unity which is mandrake based, i installed it to test it out and got this problem from this one. other os's have installed and showed it in grub fine. i dont know any terminal commands what so ever since only been using ubuntu forever. i just always installed 2 or 3 linuxs for different purposes. need this one back its all my games especially and not used to mandrake. dont like it

---

### Post by cheapie on 2011-01-02
Download [Super GRUB2 Disk]("http://www.supergrubdisk.org/super-grub2-disk/") and burn it to a CD. Boot from the CD. Select "Detect any OS". Once it finishes, try different options until you manage to boot Ubuntu, then run sudo update-grub from there.

---

### Post by slixz85 on 2011-01-02
> **cheapie said:**
> Download [Super GRUB2 Disk]("http://www.supergrubdisk.org/super-grub2-disk/") and burn it to a CD. Boot from the CD. Select "Detect any OS". Once it finishes, try different options until you manage to boot Ubuntu, then run sudo update-grub from there.

thanks i will try to try this. do you know where i can get unetbootin or another iso burner for flash drive that works good in rpm since that is what unity linux uses. it came with nothing and the packager manager in it timeouts so i am trying to find rpm packages or another way to install them

---

