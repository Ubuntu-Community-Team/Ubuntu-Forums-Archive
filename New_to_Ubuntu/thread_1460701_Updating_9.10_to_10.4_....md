---
title: "Updating 9.10 to 10.4 ..."
date: 2010-04-23
forum: New to Ubuntu
---

### Post by hamstermoon on 2010-04-23
I am trying to update from Jaunty to Lucid but update manager says I have a lack of free space. It is asking me to sudo apt-get clean but nothing seems to happen when I put that  into the terminal (well, apart from it wanting my password!).

Any suggestions?

The computer claims I have 60 gig free space so I must be doing something wrong somewhere!!

---

### Post by warfacegod on 2010-04-23
```
sudo apt-get autoremove
```

---

### Post by plucky on 2010-04-23
> **hamstermoon said:**
> I am trying to update from Jaunty to Lucid but update manager says I have a lack of free space. It is asking me to sudo apt-get clean but nothing seems to happen when I put that  into the terminal (well, apart from it wanting my password!).

Any suggestions?

The computer claims I have 60 gig free space so I must be doing something wrong somewhere!!


Remember to backup your data before upgrading.

Anyway,please post output from a terminal for ```
sudo fdisk -l
df -h
```

Good Luck

---

### Post by hamstermoon on 2010-04-25
> **plucky said:**
> Remember to backup your data before upgrading.

Anyway,please post output from a terminal for ```
sudo fdisk -l
df -h
```Good Luck

I did this yesterday when I was talking to my friendly geek and he says I have too little of something and need to use a Live CD to expand something or other. I have invited him round for a meal so he can do it for me!!

---

