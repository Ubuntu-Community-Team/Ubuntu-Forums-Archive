---
title: "[Ask]Firewall"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by sibl4ck on 2010-10-24
Hello all
I newbe
To The Point
for some reason in the necessity of work, I am required to turn off the firewall when I'm working.

Question:

Is Ubuntu desktop has a firewall?
If there
How to disable it?
and
How to activate it back?

i need u'r advice
I'm using ubuntu 10. 10

Br
Bl4ck

---

### Post by gandaran on 2010-10-24
install a simple gui to use, "gufw" find it in software center or synaptic

---

### Post by CharlesA on 2010-10-24
^ that.

Else you can just run:

```
sudo ufw enable
```

To enable the firewall.

And then run:

```
sudo ufw disable
```

To disable it.

---

### Post by krishnandu.sarkar on 2010-10-24
I think firewall is by default disabled on Ubuntu. Can someone please confirm this??

---

### Post by CharlesA on 2010-10-24
> **krishnandu.sarkar said:**
> I think firewall is by default disabled on Ubuntu. Can someone please confirm this??

That is correct.

---

### Post by sibl4ck on 2010-10-24
Great advice
thnx all ^_^

---

### Post by krishnandu.sarkar on 2010-10-24
> **CharlesA said:**
> That is correct.

Thanks :)

---

