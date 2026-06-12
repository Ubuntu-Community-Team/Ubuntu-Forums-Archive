---
title: "cant install network manager gnome"
date: 2006-09-30
forum: Networking &amp; Wireless
---

### Post by ymitis on 2006-09-30
I have tried: sudo apt-get install network-manager-gnome
Response:  Reading package lists...Done
building dependency tree... Done
E: Couldn't find package network-manager-gnome

What am I doing wrong?

---

### Post by aarbear26 on 2006-09-30
i believe its actually networkManager or NetworkManager, there is no -
hope that helps some

---

### Post by wieman01 on 2006-09-30
Could be a problem with your respositories. Run this command line from a terminal window:
> sudo gedit /etc/apt/sources.list
Make sure these lines are there:
> # Ubuntu 'Main' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

# Ubuntu 'Universe' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
Then save and run the command again:
> sudo apt-get install network-manager network-manager-gnome
That installs NetworkManager and the GUI (= network-manager-gnome).

---

### Post by ymitis on 2006-09-30
Thanks for your help, I will try that

---

### Post by ymitis on 2006-09-30
You guys are awsome! That worked.  Thanks for helping a beginner like me

---

