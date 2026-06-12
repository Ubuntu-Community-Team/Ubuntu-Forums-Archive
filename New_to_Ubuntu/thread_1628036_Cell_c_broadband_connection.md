---
title: "Cell c broadband connection"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by Dnmac on 2010-11-22
I have just done an installation of Ubuntu10.10. I cant get my Cell C broadband wireless modem to work. I am an absolute beginner so a step by step guide would be appreciated. Thanks:p

---

### Post by cariboo on 2010-11-22
What is the output of dmesg, when you plug your modem in? Open an Applications->Accessories->Terminal and type:

```
dmesg | tail -n20 > dmesg.txt
```

The above command creates a text file called dmesg.txt, that you can copy to your Windows partition and paste in your next post.

---

### Post by Dnmac on 2010-11-23
the message I get when I type in what you suggested is dmesg [-c] [-n level] [-r] [-s bufsize] please bear in mind that I am running two computers at the moment one with windows which is the one I am connected to at the moment and the other one which has Ubuntu on it . This is the one I cant connect to the internet at the moment. Thanks Derek

---

