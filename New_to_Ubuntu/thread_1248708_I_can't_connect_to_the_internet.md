---
title: "I can't connect to the internet"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by Mark95 on 2009-08-24
I just installed Ubuntu onto an 8 year old Dell Dimension 4300S system this afternoon. I can't connect to the internet, what do I do? This computer doesn't seem to have an Ethernet port. :confused:

---

### Post by LewRockwell on 2009-08-24
install NIC

.

---

### Post by zkriesse on 2009-08-24
Does it have an internal wireless card or can you buy a wireless USB adapter?

---

### Post by Mark95 on 2009-08-24
1. What is an NIC?

2. I have a USB modem, but it is wired.

---

### Post by zkriesse on 2009-08-24
Ok....can you get or borrow from a friend a usb wireless?

---

### Post by Mark95 on 2009-08-24
What's a USB wireless? :redface:
I don't think this computer has built in Wireless support, it's old.
Does internet have to be wireless?

---

### Post by LewRockwell on 2009-08-24
> **Zachk18 said:**
> Ok....can you get or borrow from a friend a usb wireless?

where do you see that the OP has access to wireless?

to OP:

NIC = Network Interface Card

that thingy where you might plug in a wired LAN connection

LAN = Local Area Network

.

---

### Post by Mark95 on 2009-08-24
All I have is a Cable modem, with USB and Ethernet, and a wireless router, with only ethernet. 
My computer doesn't have an ethernet port for some bizarre reason, and my USB connection isn't working. It used to work with this computer when I had XP.

---

### Post by zkriesse on 2009-08-24
> **LewRockwell said:**
> where do you see that the OP has access to wireless?

to OP:

NIC = Network Interface Card

that thingy where you might plug in a wired LAN connection

LAN = Local Area Network

.
 
Simple question man.....relax and just try to help the guy.

---

### Post by miwaypet on 2009-08-24
In terminal 

```
ifconfig
```

Post output here (copy and paste)

---

### Post by zerhacke on 2009-08-24
> **Mark95 said:**
> All I have is a Cable modem, with USB and Ethernet, and a wireless router, with only ethernet. 
My computer doesn't have an ethernet port for some bizarre reason, and my USB connection isn't working. It used to work with this computer when I had XP.

Windows is about the only OS that will have drivers for USB cable modems.  Even if there were drivers for it, you would need to get on the net to download the drivers for your modem in order to... get online.  It's a catch 22.

NICs are cheap.  Go buy a good 10/100 NIC from a reputable dealer.  Linux picks up almost every NIC made these days.  Get a length of CAT5 and connect to your modem to the NIC.

---

