---
title: "My Wireless works on Ubuntu but not in Kubuntu"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by heroidi on 2009-07-13
Please help i don't know what to do.

---

### Post by Kobalt on 2009-07-13
Then please help us and describe your issue a little bit further... :)

---

### Post by carml on 2009-07-13
What are the spec. of your PC?

---

### Post by heroidi on 2009-07-13
My specs:
768 MB RAM, 128 Graphic card, 20 GB hard drive 2.8 GB SWAP 2.4 Ghz, and a Wireless card witch's drivers i install with NDISWRAPPER

EDIT:
it worked before in other releases of Ubuntu

---

### Post by carml on 2009-07-13
Do you know the model of your wireless card? If not can you please post the result of ```
lspci | grep Ethernet 
``` the symbole after lspci is a vertical dash not a 1 or a lower-case L :)

---

### Post by heroidi on 2009-07-13
Right now i'm @ work so i can't do it i'll try if i am able to go and get the result somehow

EDIT:
I subscribed the thread and i'll post later the result :D

---

### Post by heroidi on 2009-07-13
the output of is lspci | grep Ethernet
output:

02:01.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by heroidi on 2009-07-14
help.... someone

---

### Post by tarps87 on 2009-07-14
When you say it worked in Ubuntu but not Kubuntu, did you just install the kde packages or did you upgrade the versions?

Do you know that the driver is working? 

**If you don't know**

Can you post the output of
```
iwconfig
```

**If you do can try installing wicd**

If you have a wired connection you can try installing wicd
```
sudo apt-get install wicd
```

It should automatically replace the default network manager, if not you need t edit the start up applications. Unfortunately I can not remember how to do this in kde, I think it is under system settings.
You will need to remove the existing network manager and add the command wicd-client.

I know there are some cases where the default network app doesn't work well with some cards.

---

### Post by heroidi on 2009-07-14
it works with wicd now thanks

---

