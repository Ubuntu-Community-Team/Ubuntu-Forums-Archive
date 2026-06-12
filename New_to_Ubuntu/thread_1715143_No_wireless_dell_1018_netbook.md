---
title: "No wireless dell 1018 netbook"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by bessy on 2011-03-26
Hi, i have downloaded ubuntu 10.10 netbook remix for my dell inspiron 1018 mini and everything works great, except i cannot get the wifi working. i have tried following instructions from doing a search but none the wiser. if anyone could give me a helping hand it would be much appreciated. 

many thanks bess.

---

### Post by tushar maroo on 2011-03-26
have you updated the ubuntu 10.10 after installing???tell me full description or try manually adding wireless via manual adding from network connections.

---

### Post by bessy on 2011-03-26
> **tushar maroo said:**
> have you updated the ubuntu 10.10 after installing???tell me full description or try manually adding wireless via manual adding from network connections.

I have updated, but still no wireless. I have tried adding wireless from network connections, but doesn't even pick up any wifi.

---

### Post by tushar maroo on 2011-03-26
here i found solution for you hope that will help you out
[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/my-dell-inspiron-mini-1018-wireless-is-not-working-859293/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/my-dell-inspiron-mini-1018-wireless-is-not-working-859293/)

---

### Post by bessy on 2011-03-26
Hi , i have tried copy and pasting this into terminal
    sudo add-apt-repository ppa:lexical/hwe-wireless

    sudo apt-get update

    sudo apt-get install rtl8192ce-dkms

as suggested but still have no wireless? is there anything i have to do after?

thanks bess.

---

### Post by tushar maroo on 2011-03-26
you should try......
[http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html)

---

### Post by bessy on 2011-03-26
Thamks for replies, i think the problem is that the latest 1018 uses a different wireless card to that. have tried both methods with no luck.
Do i just copy and paste this into terminal? and do i have to do anything after for it to activate?


    sudo add-apt-repository ppa:lexical/hwe-wireless

    sudo apt-get update

    sudo apt-get install rtl8192ce-dkms

---

