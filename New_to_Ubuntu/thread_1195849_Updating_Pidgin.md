---
title: "Updating Pidgin"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by rednight69 on 2009-06-24
How do I update pidgin to the newest version, tried just copy and pasting into the terminal from what the site said and last time I tried, ended up corrupting my system. Could I get some help with this please?

running on version 8.10

---

### Post by kostkon on 2009-06-24
Do you mean you are trying to follow what [this page]("http://pidgin.im/download/ubuntu/") says?

The thing is that these are two commands, so you have to give them separately, that is, you first give this
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
```
if everything goes ok, then you give the following
```
echo deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu `lsb_release --short --codename` main | sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
```

---

### Post by jmszr on 2009-06-24
rednight69.

Edit: Mistaken answer.

---

### Post by rednight69 on 2009-06-24
> **kostkon said:**
> Do you mean you are trying to follow what [this page]("http://pidgin.im/download/ubuntu/") says?

The thing is that these are two commands, so you have to give them separately, that is, you first give this
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
```if everything goes ok, then you give the following
```
echo deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu `lsb_release --short --codename` main | sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
```


after the 2nd line, is it supposed to say anything or no?

---

### Post by kostkon on 2009-06-24
> **rednight69 said:**
> after the 2nd line, is it supposed to say anything or no?
No. 

After giving these commands, you can open the update manager (*System &#8594; Administration &#8594; Update Manager*) and check for updates. You should get an update notification for *Pidgin* to update to the latest version.

---

### Post by rednight69 on 2009-06-25
yay, thankie so much, got it working and updated

---

