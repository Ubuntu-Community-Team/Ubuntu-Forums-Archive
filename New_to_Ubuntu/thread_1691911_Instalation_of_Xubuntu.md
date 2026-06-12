---
title: "Instalation of Xubuntu"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by anotherdummhead on 2011-02-20
Good evening everyone.

I apologise for opening this theme, i'm really new in Linux world and this is my 3rd time i'm switching from XP to Xubuntu, but i never had luck to actually do everything as i want.

Long story short, i want to erase all of my 3 partitions that i have and create 3 totally new Ext4 primary partitions. My questions are :

1. For Filesystem partition i use mountpoint "/" and what mountpoint should i use for the other two ?

2. Besides these 3 partitions, i want to create a swap partition, how do i do that ?

I'm currently waiting for your answer, and i booted my LiveCD

[http://www.zimagez.com/zimage/screenshot-02202011-090703pm.php](http://www.zimagez.com/zimage/screenshot-02202011-090703pm.php)
[IMG]http://www.zimagez.com/zimage/screenshot-02202011-090703pm.php[/IMG]

---

### Post by Dutch70 on 2011-02-20
> **anotherdummhead said:**
> Good evening everyone.

I apologise for opening this theme, i'm really new in Linux world and this is my 3rd time i'm switching from XP to Xubuntu, but i never had luck to actually do everything as i want.

Long story short, i want to erase all of my 3 partitions that i have and create 3 totally new Ext4 primary partitions. My questions are :

1. For Filesystem partition i use mountpoint "/" and what mountpoint should i use for the other two ?

2. Besides these 3 partitions, i want to create a swap partition, how do i do that ?

I'm currently waiting for your answer, and i booted my LiveCD

all you really need is 2 ptns, but 3 is better. 

1. swap = similar to page file
2. "/" root = where the Xubuntu system is.
3. /home = Docs, Pics, vids, music etc. along with .config files.

if you want another one, it depends on what you want it for.

ps. how big is your hdd?

---

### Post by anotherdummhead on 2011-02-20
One, for the system. C\

The other one, games, files downloaded from the internet. D\

Third one, everything else, pictures, music, videos. E\

This is how it looked like on XP and i kinda want to keep it like this, is that possible and how ?

EDIT : HDD, 80GB :)

---

### Post by Dutch70 on 2011-02-20
> **anotherdummhead said:**
> One, for the system. C\

The other one, games, files downloaded from the internet. D\

Third one, everything else, pictures, music, videos. E\

This is how it looked like on XP and i kinda want to keep it like this, is that possible and how ?

EDIT : HDD, 80GB :)

Ok...it's like that huh...lol j/k

C\ = "/"
E\ = /home or Docs & settings
D\ = not sure, possibly "data"

and like I said swap = pagefile

---

### Post by anotherdummhead on 2011-02-20
You mean /data, right ?

What mountpoint should i use then ?

---

### Post by anotherdummhead on 2011-02-20
Erm...anyone?

---

### Post by mr_luksom on 2011-02-21
Yes, he means /data. Having a separate /home partition is a fantastic idea as well, it helps if you ever want to migrate computers or linux distros.

---

