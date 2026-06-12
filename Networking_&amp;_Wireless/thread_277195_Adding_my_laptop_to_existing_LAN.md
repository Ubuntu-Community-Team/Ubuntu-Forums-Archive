---
title: "Adding my laptop to existing LAN"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by JurB on 2006-10-14
Hi,

I'm trying to add my laptop to an existing lan at home. The current  network looks like this:
I have 2 boxes, one is a xp machine wich is connected to the internet using your standard adsl modem and connected to my second box (Ubuntu) trough an eth cable. Internet connection is shared between the two.
I would like to connect my laptop (Ubuntu) to the second box using a second eth card in that box. My laptop should also be able to use the shared internet connection.
Can this be done without the use of a router/ a second cable from the xp machine to my laptop? How would i configure this?

Tnx

---

### Post by dmizer on 2006-10-14
you would need a third network card in your xp machine to connect directly to it.  otherwise you would need a second network card in your first ubuntu box and configure nat via firestarter.

you shouldn't need a router to do what you want to do.  since your xp machine is already handing out a network address, it's already functioning as a router.  you could go out and purchase a very cheap networking hub and free yourself of a great deal of headache.

---

### Post by JurB on 2006-10-14
> **dmizer said:**
> otherwise you would need a second network card in your first ubuntu box and configure nat via firestarter.


That's the plan, can you give me some pointers how to actually configure firestarter?

---

### Post by dmizer on 2006-10-14
i really suggest you take a look at networking hubs.  i've been using one in my network for a year now.  i purchased it for about $5 us.

if you're dead set, try this: [https://wiki.ubuntu.com/ThinClientHowtoNAT](https://wiki.ubuntu.com/ThinClientHowtoNAT)

---

