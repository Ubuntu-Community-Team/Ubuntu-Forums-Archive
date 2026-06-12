---
title: "Unable To Locate Packages"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by Intzi1992 on 2011-09-03
I've read a lot of forum's talking about this problem.. but i still didnt find the way to fix it.. or the other's solution didnt work for me.
I try to install program's from my terminal with **apt-get** **install** and i have this message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package (And The Name Of The Program i Try To Install)

Does Any one Know How Can I Fix It?
(I Have Tried apt-get update)
(I Have Also Tried to Change Some Settings To sources.list But I Dont Know If Are Right..)

Waiting For Answers. Thx :D

---

### Post by ClientAlive on 2011-09-03
> **Intzi1992 said:**
> I've read a lot of forum's talking about this problem.. but i still didnt find the way to fix it.. or the other's solution didnt work for me.
I try to install program's from my terminal with **apt-get** **install** and i have this message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package (And The Name Of The Program i Try To Install)

Does Any one Know How Can I Fix It?
(I Have Tried apt-get update)
(I Have Also Tried to Change Some Settings To sources.list But I Dont Know If Are Right..)

Waiting For Answers. Thx :D


Does the program you are trying to install come from a repository in your list? You can google the program to find out/ track down what repo it comes from then check of if that repo is installed in synaptic by clicking "settings" then "repositories." The first two tabs tell it.

HTH

---

### Post by 2F4U on 2011-09-03
Can you tell us what program you are trying to install?

---

### Post by jzjavez on 2011-09-03
i have recently installed ubuntu and i want to install the vlc player in that for this it is asking for the packages and where will i can found them

---

### Post by oldos2er on 2011-09-03
Check to make sure you have all repositories enabled, then run ```
sudo apt-get update
```
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Leshrac on 2011-09-03
> **Intzi1992 said:**
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package (And The Name Of The Program i Try To Install)
This kind of message usually appears when you type the name of the package wrong, are you sure this is not the problem? what packages are you trying to install?

Alternatively, if you are new you might want to try out Ubuntu Software Center or synaptic for package installing, both have user interfaces that that you might find easier to use.

---

### Post by ClientAlive on 2011-09-05
> **Leshrac said:**
> This kind of message usually appears when you type the name of the package wrong, are you sure this is not the problem? what packages are you trying to install?

Alternatively, if you are new you might want to try out Ubuntu Software Center or synaptic for package installing, both have user interfaces that that you might find easier to use.


If the guy's trying to install vlc the name is actually "video-lan" I-think. Might want to check that out.

---

### Post by JRV on 2011-09-05
You should be able to install like this:

```

sudo apt-get update
sudo apt-get install vlc

```

If that does not work you probably messed up the sources.list file.  Check to see if you have a /etc/apt/sources.list.save file.

---

### Post by Enigmapond on 2011-09-05
> **ClientAlive said:**
> If the guy's trying to install vlc the name is actually "video-lan" I-think. Might want to check that out.

No..the package is VLC... sounds like the repo isn't activated...check the software center to see if it lists..

---

