---
title: "Joined Domain but cannot login when not on network"
date: 2020-01-20
forum: Networking &amp; Wireless
---

### Post by 90buntu on 2020-01-20
I have joined my laptop, that has Ubuntu 18.04 LTS installed, to my company's domain, but when I bring my laptop back home, I couldn't login.
I received an error "Access Denied".  Is there a way for my laptop to cache the password used to login to my company's domain? Or any way I can login to the domain when there is no network?

---

### Post by awebdev17 on 2020-01-20
There's an askubuntu.com thread I found from 4 an a half years ago that says logging in offline is not possible. That's a bummer and I'd be interested if there's a solution today that exists. 

The solution from that post is to create a local user to use as your main account and 'su - <domain user name>' when you're online and need to be on your domain. I don't know how practical that is, but it's a workaround anyway.

---

### Post by 90buntu on 2020-01-21
In other words, I have two options if I have a group of Ubuntu computers in my company's domain:
1. I shouldn't be joining these computers to my company's domain, as it causes problem when working offline
2. If I insist on joining the computer to the company's domain, I will then have to use Ubuntu on PCs instead of notebooks so I wouldn't have to worry about offline.  

:-(:-(:sad::sad:

---

### Post by CorporateMonkey on 2020-01-21
Your company should probably have IT specialist that could help you with your problem. It may be a good idea to talk to him.

---

### Post by 90buntu on 2020-01-22
So, can anyone explain what would be the advantage of joining Linux the computer to the company's domain, other than keeping track of inventories?

---

### Post by slickymaster on 2020-01-22
Thread moved to **Networking & Wireless** for a better fit

---

