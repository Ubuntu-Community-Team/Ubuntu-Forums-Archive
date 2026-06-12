---
title: "Driver for my graphic card?"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by grobar87 on 2010-09-10
Hi,
How to install driver for my graphic card?
When i run "lspci | grep VGA" in terminal i got this:

```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
```

Can anyone tell me how to find driver for ubuntu lucid?
Thanks.

---

### Post by llawwehttam on 2010-09-10
I thought a driver was pre-installed. No?

---

### Post by howefield on 2010-09-10
Driver should already be installed, are you having a problem with graphics ?

---

### Post by grobar87 on 2010-09-10
Yes i have problem with graphic...I've noted that the GUI rendering sometimes is slow and or kind of buggy. I have checked the restricted driver manager and there is not any driver listed there, so I suppose I should install the proprietary drivers for my Intel graphics card?
I disable compiz fusion...but still the same...:S

---

### Post by halitech on 2010-09-10
Intel doesn't have a proprietary driver so it's included in the OS for you. Guessing that since its an Intel GPU that it is onboard, how much memory is allocated to the video on your system?

---

### Post by grobar87 on 2010-09-10
> **halitech said:**
> Intel doesn't have a proprietary driver so it's included in the OS for you. Guessing that since its an Intel GPU that it is onboard, how much memory is allocated to the video on your system?

I don't know that...can you tell me how to see?

---

