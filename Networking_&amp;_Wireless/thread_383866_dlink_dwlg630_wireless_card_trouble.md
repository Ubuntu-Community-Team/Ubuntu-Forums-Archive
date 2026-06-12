---
title: "dlink dwlg630 wireless card trouble"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by chrisT on 2007-03-13
I cant get my dlink dwlg630 wireless card to work after installation of ubunta. Can anyone help!!

---

### Post by gradedcheese on 2007-03-14
Sounds like this card works, at least some versions of it: [http://www.linuxquestions.org/hcl/showproduct.php?product=2376&cat=133](http://www.linuxquestions.org/hcl/showproduct.php?product=2376&cat=133)

Please open a terminal (Applications->Accessories->Terminal) and run the following command (type it and press Enter)

```

lspci

```

In the output, find the line(s) starting with "Ethernet Controller" and paste them into a post here.  If your card says "Atheros" then you are in good shape :)  If not, then it still might work, but it depends.

---

