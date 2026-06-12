---
title: "Upgrading from xubuntu 8.04.1 to xubuntu 8.10"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by dapissarenko on 2008-12-23
Hello!

How can I upgrade xubuntu 8.04.1 to 8.10 without completely reinstalling the system?

Thanks in advance

Dmitri

---

### Post by hellomoto on 2008-12-23
> **dapissarenko said:**
> Hello!

How can I upgrade xubuntu 8.04.1 to 8.10 without completely reinstalling the system?

Thanks in advance

Dmitri

just type into a terminal:
```

sudo apt-get update
sudo apt-get dist-upgrade

```

This will upgrade you to the latest distro. :)

---

### Post by bikeboy on 2008-12-23
This ubuntu wiki page should give you all the information you require, including a few different options - [https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades)

---

### Post by ibizatunes on 2008-12-23
The is lots of ways to do it, clean install is one, make sure you backup home first!
The other is go to system > update > install all patches > reboot and install 8.10 (if the option isnt there then you need to go to software source and select non lts release ) This bit is from memory sorry

And it will pop up saying new version 8.10 is avaiable

---

### Post by dapissarenko on 2008-12-23
Thanks all for the help!

---

