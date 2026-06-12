---
title: "internet problems"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by deathscith on 2009-01-27
alright, so i have vista 64bit already installed, i then put ubuntu 8.10 64bit on a second harddrive, and since then, my vistas internet hasnt worked, ive tried doing as much as i could on there but was met with no success, ubuntu has the ip address my vista used to use, and now vista has a random one, and cant even connect to my router, and suggestions?

---

### Post by sarpulhu on 2009-01-27
Not sure if Vista still has it but try running "winipcfg" on Run prompt in Vista. It worked in older windows at least. Then refresh the IP's or set them up.

---

### Post by cariboo on 2009-01-27
Winipcfg hasn't been used since Windows 98, open up a terminal and type ipconfig to get the same results as winipcfg. Go to Start-->Run and type:

```
cmd
```

and hit enter, Once the dos window opens type:

```
ipconfig /all
```

This will give you all the inforamtion about your network connection.

To the OP, did you have to install any firmware to make your nic work?

Jim

---

### Post by sarpulhu on 2009-01-27
Wow, I haven't gone back to windows in a while...guess 98...yikes.

---

### Post by deathscith on 2009-01-27
umm, well it shows a strange IP, starting with like 16x.x.x.x when its normally 192.x.x.x and what do you mean nic?

sorry it took so long to reply lol, i went and took a nap

---

