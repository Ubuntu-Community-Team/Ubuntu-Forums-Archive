---
title: "Internet in 7.04"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by liquidfunk on 2007-08-02
Just trying the Live CD of 7.04, It can see my network, but I cannot physically connect to it. The green lights never come on. No Internet.

 Any ideas.

---

### Post by walkerk on 2007-08-02
> **liquidfunk said:**
> Just trying the Live CD of 7.04, It can see my network, but I cannot physically connect to it. The green lights never come on. No Internet.

 Any ideas.

what network card do you have?

```
lspci | grep Network
```

---

### Post by liquidfunk on 2007-08-02
Linksys WUSB54GR. 

 Works with NDISwrapper on 6.10, thats what I am on now.

 Just wanted to upgrade.

---

### Post by Junglizer on 2007-08-02
What version of Linksys? 


Sweet name btw.

---

### Post by walkerk on 2007-08-02
> **liquidfunk said:**
> Linksys WUSB54GR. 

 Works with NDISwrapper on 6.10, thats what I am on now.

 Just wanted to upgrade.

Hmm.. I don't think you previous ndiswrapper will work on the LiveCD.. I think you just need to jump into 7.04.. if youre just upgraded I think you'll ndiswrapper and driver will work OK from Edgy Eft..

Could be wrong but the LiveCD internet never works for me..

---

### Post by liquidfunk on 2007-08-02
Right, so is there a reason why I can see the network but not connect?

---

### Post by walkerk on 2007-08-02
> **liquidfunk said:**
> Right, so is there a reason why I can see the network but not connect?

If I remember correctly, I could see the networks as well... just couldn't connect. Not sure.. are you trying to connect to a secured network?

---

### Post by liquidfunk on 2007-08-02
Nope.

---

### Post by walkerk on 2007-08-02
> **liquidfunk said:**
> Nope.

Not sure man. Like I said I've never been able to connect to  my wireless using the Live CD.. even with a working version of Ubuntu.. Sorry.

Perhaps someone else has some insight..

---

