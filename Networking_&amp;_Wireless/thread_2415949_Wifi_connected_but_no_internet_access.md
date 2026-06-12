---
title: "Wifi connected but no internet access"
date: 2019-04-03
forum: Networking &amp; Wireless
---

### Post by pratap73 on 2019-04-03
Tried everything avail on forums

---

### Post by kc1di on 2019-04-03
Lets start with your wifi card?  Go to a terminal and type this command if you don't know the card you have. ```
lshw -C network
```

or download and run the wireless script in my signature.

---

### Post by howefield on 2019-04-03
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by pratap73 on 2019-04-03
Can't able to download any script bc no wired internet working!!

---

### Post by kc1di on 2019-04-03
> **pratap73 said:**
> Can't able to download any script bc no wired internet working!!

What does the command I asked you to run in a terminal output? 
Or at least give us your wireless card model , manufacturer.

---

### Post by pratap73 on 2019-04-04
PRODUCT: AR9485 Wireless Network Adapter
Vendor: Qualcomm Atheros
Physical Id: 0
Bus info : pci@0000:01:00:0
Logical name: wlo1
Version: 01
Serial: 24:fd:52:f8:35:c0
Is it sufficient info ?
One more that no usb cable is working tho, not able to connect my phone thru usb cable

---

### Post by kc1di on 2019-04-04
Thank You for the info.  Here are some things you can try.
Go to Network Manager and wifi settings disable IPV6.  see if you can get Internet through put then.  Make sure your set to WPA not WEP authentication. 
Also does your router have any kind of fire wall enabled. Those are a few things to try first.

---

### Post by pratap73 on 2019-04-04
Where to check firewall

---

### Post by pratap73 on 2019-04-04
Activation of network connection falied

---

### Post by kc1di on 2019-04-04
if activation fail with no IPV6 then reenable it.  if it fails with WPA you may have to reset your router to wpa. If you have a firewall built into the router you will have to access the router control and either disable it or create a rule to allow your machine IP to access it.

---

