---
title: "Problem with Internet Connection"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by Ryklou on 2008-06-19
My internet connection on Ubuntu wont work, i have 2 other pc's in the house so i know it's not the router.  When i run Firefox, it say's that it cannot connect to the server, when i start Firestarter, it has an error. (I'll post it when i get home tonight, but it relates to the ethernet cable or something not being found.) NO internet connection, what so ever.

If any body can help me, please do.

tnx

~francois
[FONT="Courier New"][SIZE="1"](I'll add screenshots, and more data when i get home.)[/SIZE][/FONT][-o<

---

### Post by AVT- on 2008-06-19
Have you ever connected to the internet with this system? If you have, when did this problem start?

---

### Post by Ryklou on 2008-06-19
This is "my" only system. i have been connected to it. it stopped working yesterday night, you think it could be firestarter, cause i downloaded that last then i restarted my system.

---

### Post by AVT- on 2008-06-19
Since this started once you installed Firestarter, it's probably the same problem I had a few days ago, iptables blocking you from accessing anything.

Try

> sudo apt-get purge iptables

Note that this will remove Firestarter, and maybe a few other things as well. 

If this fixes it, reinstall Firestarter, and use it to configure iptables to let you access the internet.

---

### Post by Ryklou on 2008-06-19
Like what other things? lol

---

### Post by AVT- on 2008-06-19
Anything that depends on iptables. It'll tell you what will be removed, so you can write it down, or something, and reinstall after, if you want.

---

### Post by Ryklou on 2008-06-19
cool coll thank you, i'll try it when i get home :0
:KS

---

### Post by Ryklou on 2008-06-19
boo ! your code still didn't make me able to get online, so like i always do i reformatted, and will never, try that code again lol. Thank's for trying to help me tho.:lolflag:
[ATTACH]74665[/ATTACH]

---

### Post by molotov00 on 2008-06-19
> **Ryklou said:**
> boo ! your code still didn't make me able to get online, so like i always do i reformatted, and will never, try that code again lol. Thank's for trying to help me tho.:lolflag:
[ATTACH]74665[/ATTACH]

Haha. You can't be serious about fixing a problem if the first thing you do is format. I feel like I waste my time when I help people like you. I'm glad I didn't this time.

---

### Post by Ryklou on 2008-06-20
> **molotov00 said:**
> Haha. You can't be serious about fixing a problem if the first thing you do is format. I feel like I waste my time when I help people like you. I'm glad I didn't this time.

well all i do almost every day i go online. and i needed to do something. i just installed Ubuntu i reinstalled it twice. last time i re-installed it i accedently used code:
```
sudo chown root:root /
```

---

