---
title: "trying to install usb-creator, can't find package"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by woodsonoversoul on 2010-02-16
What does that mean?

---

### Post by k3lt01 on 2010-02-16
> **woodsonoversoul said:**
> What does that mean?Could you give us more information?

---

### Post by woodsonoversoul on 2010-02-16
```
:~/usb-creator-0.1.10/bin$ sudo apt-get install usb-creator
[sudo] password for dan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package usb-creator

```

---

### Post by werecatomega on 2010-02-16
it means that the program "usb-creator" is not a program

---

### Post by k3lt01 on 2010-02-16
> **woodsonoversoul said:**
> ```
:~/usb-creator-0.1.10/bin$ sudo apt-get install usb-creator
[sudo] password for dan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package usb-creator

```

Go to synaptic and install it from there.

What version of Ubuntu are you using? If you ar using Feisty I don't think it was available.

---

### Post by woodsonoversoul on 2010-02-16
Synaptic can't find it either. I'm using Hardy BTW...

---

### Post by k3lt01 on 2010-02-16
> **woodsonoversoul said:**
> Synaptic can't find it either. I'm using Hardy BTW...Ok, it was available in Hardy but only from the Backports repository, so you need to enable Backports then refresh your sources list and then install it.

---

### Post by woodsonoversoul on 2010-02-16
Worked like a charm. Thanks man.

---

