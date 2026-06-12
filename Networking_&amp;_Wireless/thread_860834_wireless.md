---
title: "wireless"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by ddg on 2008-07-16
Help needed,

I installed ubuntu 8.04 64 bit on Acer 6291. Spec:
Centrino Duo (Core2 duo). 512 MB ram and 120 GB disk. Intel graphic and Intel wireless.

Every thing went well and every device is detected. The problem is that wireless not working well. Some time it shows signal indicator but it can not connect. When I swicth the button (led indicator is never on) it shows searching status for the signal and it found the network but it never connect.

I am new to linux and trying to understand the command line. Please give me step by step hint.

Regards,
ddg

---

### Post by ddg on 2008-07-16
> **ddg said:**
> Help needed,

I installed ubuntu 8.04 64 bit on Acer 6291. Spec:
Centrino Duo (Core2 duo). 512 MB ram and 120 GB disk. Intel graphic and Intel wireless.

Every thing went well and every device is detected. The problem is that wireless not working well. Some time it shows signal indicator but it can not connect. When I swicth the button (led indicator is never on) it shows searching status for the signal and it found the network but it never connect.

I am new to linux and trying to understand the command line. Please give me step by step hint.

Regards,
ddg
Hi There,

I decided to reinstall with Ubuntu 7.10 and every thing is working. The wireless, wired ethernet, the graphic adapter all are good.

For time being I gave up with Ubuntu 8.04, may be next time.

I have one question only and it is about error message at the booting stage.

It shows:
[ xxxxxxxx] PCI: can not allocate source bla bla........

xxxx is representing some digits.

There are 7 lines of it, it moves very fast so I can not catch exactly what it says.
Please give me some tips how can I get rid of it.
Regards,
ddg

---

### Post by chili555 on 2008-07-16
The first step is to pin down what the message really is. Open a terminal and type:```
dmesg | grep allocate
```Let's see what the 'bla bla' is telling us.

Please post the result here.

---

### Post by ddg on 2008-07-17
> **chili555 said:**
> The first step is to pin down what the message really is. Open a terminal and type:```
dmesg | grep allocate
```Let's see what the 'bla bla' is telling us.

Please post the result here.

Hi Chili555,

Here it is the 'bla ..bla'
Ahaa, I can reproduce the error message with the command.
[   15.625367] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[   15.625426] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   15.625482] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[   15.625538] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[   15.625594] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[   15.625651] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[   15.625707] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[   15.625763] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[   15.625820] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
[   16.818498] Cannot allocate resource for EISA slot 1
[   16.818502] Cannot allocate resource for EISA slot 2


Regards,
ddg

---

### Post by chili555 on 2008-07-17
This is a well-known bug: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/54294](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/54294)

See the very last post:> The solution is the kernel 2.6.25I don't know when we will get 2.6.25.

Evidently, although the errors are thrown up, it causes no harm and the computer boots normally. I suggest you live with it for now.

---

### Post by ddg on 2008-07-17
> **chili555 said:**
> This is a well-known bug: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/54294](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/54294)

See the very last post:I don't know when we will get 2.6.25.

Evidently, although the errors are thrown up, it causes no harm and the computer boots normally. I suggest you live with it for now.

Hi Chili555,

I think you are right. Every thing is working well. I will stay with it for time being. 
Thanks,
ddg

---

