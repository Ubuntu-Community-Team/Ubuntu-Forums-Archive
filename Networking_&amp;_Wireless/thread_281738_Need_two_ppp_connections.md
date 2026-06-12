---
title: "Need two ppp connections"
date: 2006-10-21
forum: Networking &amp; Wireless
---

### Post by Amar_ze on 2006-10-21
Hi all. I am tryng to set up two ppp connections(ppp0, ppp1) ofcourse with pppoeconf.Is it possible? I will use ppp0 for "regular" net and ppp1 will be used for one kind of "free zone" as my ISP calls it.It's like LAN with IP's 10.x.x.x and we can download for free from their server(as we have dl limits).So I will do route add some.ip.addres ppp1 (IP's will be from etc. news server,ftp ...) and route addd default ppp0 so for everything else.So except those IP's will go thru ppp0.I hope i was clear about this one.main question: how to make ppp0 and ppp1 to be up at same time.Thanks :)

Edit:

I am allready using this two type of conn. just not in same time :). I made dsl-provider and dsl-provider-free so I do pon dsl-provider and pon dsl-provider-free as I need first or second one.So only thing I need is how to make this two work in same time

---

### Post by Amar_ze on 2006-10-21
Anyone with ideas? Any idea is more than wellcome

---

### Post by christhemonkey on 2006-10-21
Can you not:
```
pon dsl-provider dsl-provider-free 
```

?

---

### Post by Amar_ze on 2006-10-21
No. Nothing happens. I tryed starting one then second but ppp0 is up and stay same. I need ppp0 and ppp1 at same time

---

