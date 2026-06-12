---
title: "Multiple graphic cards"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by Electromechanical Magpie on 2010-07-24
I have a fairly wierd system with three different graphic cards. The cards are:

[LIST]
[*]One ATI Radeon HD4870
[*]One ATI X1600
[*]and a 14 year old S3 card
[/LIST]
Is there a way to use all three cards at the same time in linux?

---

### Post by cariboo on 2010-07-25
Are all three cards recognized when you run:

```
lspci
```

and

```
sudo lshw
```

Personally If the S3 card is a stand alone, I'd remove it, as there is only vesa support for it.

---

