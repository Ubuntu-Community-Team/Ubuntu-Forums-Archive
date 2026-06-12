---
title: "Can't get wireless to work"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by lotuscarsltd52 on 2010-01-15
I recently reinstalled Ubuntu after using Wubi and losing it because it got screwed-up. So far Ubuntu runs fine except I cannot use the wireless internet at all (I am using an Acer netbook for those who are wondering).

At the top of the screen I don't see *anything* regarding the networks. No "monitor" icons, nothing. I checked the netbook's wireless shutoff switch thing and that did nothing. I looked for wireless networks and found nothing.

I was hoping for an easy fix to this problem. I don't like messing around with programming and terminals, etc. so I was hoping that I could easily get the wireless up and running.

Thanks

---

### Post by stoogiebuncho on 2010-01-15
What has worked for me in the past is the following:

1) Connect to the internet via a wired connection.
2) Open the update manager (System > Administration), check for updates, install everything.
3) Go to System > Administration > Hardware Drivers (or something like that)
4) If there is a driver there for your wireless card, install it.
5) If not, restart your computer, then go back to Hardware Drivers and see if there is something there now.


If these steps don't work, you'll need to tell us more about your wireless card.  Open a terminal (Applications > Accessories > Terminal) and enter the following

If you have an internal wireless card:
```
lspci
```

If you have a USB wireless card:
```
lsusb
```

Paste the output back here.

---

### Post by lotuscarsltd52 on 2010-01-15
> **stoogiebuncho said:**
> What has worked for me in the past is the following:

1) Connect to the internet via a wired connection.
2) Open the update manager (System > Administration), check for updates, install everything.
3) Go to System > Administration > Hardware Drivers (or something like that)
4) If there is a driver there for your wireless card, install it.
5) If not, restart your computer, then go back to Hardware Drivers and see if there is something there now.


If these steps don't work, you'll need to tell us more about your wireless card.  Open a terminal (Applications > Accessories > Terminal) and enter the following

If you have an internal wireless card:
```
lspci
```If you have a USB wireless card:
```
lsusb
```Paste the output back here.

SMBus: Intel Corp. 82801G (ICH7 Family) SMBus Controller (rev 02)
Network controller: Broadcom Corp. BCM4312 802.11b/g (rev 01)
Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)

---

### Post by stoogiebuncho on 2010-01-15
Hmmm.  I'm pretty sure the Ubuntu Broadcom wireless driver should work with your card.  I assume you followed the steps above to install the driver from Hardware Drivers?  It's important that you are connected to the internet when you do them or else there won't be any driver options there.

---

### Post by lotuscarsltd52 on 2010-01-15
> **stoogiebuncho said:**
> Hmmm.  I'm pretty sure the Ubuntu Broadcom wireless driver should work with your card.  I assume you followed the steps above to install the driver from Hardware Drivers?  It's important that you are connected to the internet when you do them or else there won't be any driver options there.

I looked but found no hardware drivers.

---

### Post by canthus13 on 2010-01-15
I have the exact same card.  When I installed Karmic, I had to connect via ethernet, run updates (System > Administration > Update Manager), and then install the restricted drivers (System > Administration > Hardware Drivers). (Two drivers show up for this card.  the STA driver is the one I used, and it works beautifully.)

--Me

---

### Post by lotuscarsltd52 on 2010-01-15
> **canthus13 said:**
> I have the exact same card.  When I installed Karmic, I had to connect via ethernet, run updates (System > Administration > Update Manager), and then install the restricted drivers (System > Administration > Hardware Drivers). (Two drivers show up for this card.  the STA driver is the one I used, and it works beautifully.)

--Me

So basically just plug into a wired connection, get connected, and then try these steps?

---

### Post by stoogiebuncho on 2010-01-15
> **lotuscarsltd52 said:**
> So basically just plug into a wired connection, get connected, and then try these steps?
Yes.

---

### Post by lotuscarsltd52 on 2010-01-15
> **canthus13 said:**
> I have the exact same card.  When I installed Karmic, I had to connect via ethernet, run updates (System > Administration > Update Manager), and then install the restricted drivers (System > Administration > Hardware Drivers). (Two drivers show up for this card.  the STA driver is the one I used, and it works beautifully.)

--Me

The Broadcom STA driver is shown as being activated but not in use. How do I get it working?

---

