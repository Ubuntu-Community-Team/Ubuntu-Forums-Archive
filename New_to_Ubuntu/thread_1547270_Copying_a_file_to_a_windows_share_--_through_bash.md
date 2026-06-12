---
title: "Copying a file to a windows share -- through bash"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by B34ST1Y on 2010-08-06
Hi,



I want to be able to copy a log file I have across the network to a safe location. I was wondering if someone can get me started or help me out with a way entirely through bash to do this??


thx :)

---

### Post by B34ST1Y on 2010-08-06
shameless bump for help :)

---

### Post by mapes12 on 2010-08-06
There are easier ways to do this without the need for bash............

What is your LAN configuration?

---

### Post by endotherm on 2010-08-06
should be somthing like this:

```
sudo apt-get install smbfs
mkdir ~/tmp
mkdir ~/sav
sudo smbmount //<smbservername>/<sharename> ~/tmp/ -o username=<user>,password=<pass>,rw
cp -r ~/tmp/ ~/sav/
```

---

