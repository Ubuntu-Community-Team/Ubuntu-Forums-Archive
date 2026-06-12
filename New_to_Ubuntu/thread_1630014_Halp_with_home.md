---
title: "Halp with home"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by bj218 on 2010-11-24
I have added 3 pictures I hope will help explain my problem!! I tried to
move home to another partition but was not successful. Fig no number is a picture of this partition taken today. Fig2 is a picture of what I think this partition looked like a few days ago. Fig1 is a picture of what it looks like today. My problem now is how do I get a good bill into
ubuntu? One thing I noticed to day is that a lot of the items have a 
white X by them and you cant view them?

---

### Post by cariboo on 2010-11-26
I would suggest you check ownership and permissions in your /home/Bill directory. I did something similar on a system running XBMC, and forgot tot check ownership and permissions, nothing worked the way it should. To solve the problem I opened a terminal and set the ownership and permission properly. Type the following commands in a terminal:

```
sudo chown -R bill:bill /home/bill
``` 

to take ownership of the directories and file. Next:

```
sudo chown -R 755 /home/bill
```

to set the proper permissions. You may get some errors, but it's ok to ignore them.

---

### Post by bj218 on 2010-11-26
> **cariboo907 said:**
> I would suggest you check ownership and permissions in your /home/Bill directory. I did something similar on a system running XBMC, and forgot tot check ownership and permissions, nothing worked the way it should. To solve the problem I opened a terminal and set the ownership and permission properly. Type the following commands in a terminal:

```
sudo chown -R bill:bill /home/bill
``` 

to take ownership of the directories and file. Next:

```
sudo chown -R 755 /home/bill
```

to set the proper permissions. You may get some errors, but it's ok to ignore them.
This didn't work probably because I was using my inst. disk. I don't 
think there is any way to get to the inst. program!! maybe i should
just reinstall ubuntu?

---

