---
title: "wifi problems"
date: 2013-12-22
forum: Networking &amp; Wireless
---

### Post by shresthasumit55 on 2013-12-22
i installed ubuntu 12.10 in my laptop.......but the wifi is not working it....there are no any wireless connection options.....also ran ubuntu 13.10 from live cd.....faced the same problem......i am using dell inspiron 3421.....some suggestions plzz???

---

### Post by varunendra on 2013-12-23
Welcome to the forums !

To be able to offer a suggestion, we need to know about your wireless card.

Please open a terminal (Ctrl-Alt-T) and run the following commands in it -
```
uname -mr
lspci -nnk | grep -iA2 net
```
..and post back their outputs here in your next post.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

