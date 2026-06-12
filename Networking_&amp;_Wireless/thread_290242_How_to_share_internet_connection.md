---
title: "How to share internet connection ??"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by amitava82 on 2006-10-31
i just moved to Ubuntu 6.06 :D  everything working just great (except my laptop's inbuilt Card reader. if someone knows the solution plz give link). i'm slowly shifting to ubuntu 8)

**ok here is the situation:**

i have direct cable internet connection which is attached to a hub (not Router). my computer and another four computers are also attached to that hub. the internet connection needs a  fixed IP in order to get Connected ( 10.18.106.18 )(also needs a dialer in windows, but strangely in linux its working without user id and password). so my linux machine use this IP to get connected to internet. other computers (Windows PCs) use 10.18.106.XXX IPs. I have one LAN card and i don't want to invest any more..

so how do i share the internet connection with other Win PCs? someone please tell me the easiest way to do that in step by step as u can see i'm new. :roll:  thanks for reading my post.

---

### Post by amitava82 on 2006-11-01
nobody knows? now im posting from Windows coz my network users can not browse internet if im on linux.. what a shame to be back to Win.. ](*,)

---

### Post by bluenova on 2006-11-01
Use [Firestarter](http://www.fs-security.com/)

```
sudo aptitude install firestarter
```

The first time you run the application it will ask you to set it up, including internet sharing. On the Window$ machines, do the internet sharing thing and set them as clients.

---

