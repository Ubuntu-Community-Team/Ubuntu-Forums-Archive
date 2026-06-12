---
title: "sudden unexplainable problem connecting wireless internet"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by hortstu on 2010-03-15
My linux laptop won't connect to the wireless internet.  It has used this connection many times before and there is nothing wrong with the service.  There is an apple and windows computer using it now w/o a problem.

Any suggestions on how to solve or troubleshoot this?  Thanks

---

### Post by hortstu on 2010-03-15
Never mind after multiple restarts it's working again... as unexplainable to me as the problem.

---

### Post by wannabegeek on 2010-03-17
I'm having  similar  behavior...

Wireless usually works fine.....all of a sudden, it's disconnected, then asks
for my network password, which it shouldn't need....

I'm completely down right now :(

update------

now it works again !   I hate this ....

---

### Post by 3rdalbum on 2010-03-17
> **hortstu said:**
> My linux laptop won't connect to the wireless internet.  It has used this connection many times before and there is nothing wrong with the service.  There is an apple and windows computer using it now w/o a problem.

You mean 'wireless network', I think. Wireless internet is Mobile Broadband, which operates off mobile phone towers.

Try turning down the transmission rate for your wireless card:

```
sudo iwconfig wlan0 rate 5.5M
```

EDIT: If you *are* talking about mobile broadband, then I'd advise you to upgrade to Ubuntu 10.04 (the first beta comes out in two days if you want to test, or the release comes out in a month). It fixes some known problems with mobile broadband reliability.

---

