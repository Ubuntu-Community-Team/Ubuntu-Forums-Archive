---
title: "Firestarter preventing me to access shared folder"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by Dimension7 on 2007-12-27
I am trying to access my Ubuntu's shared folder via my Macbook.  If I stop the Firestarter, I am able to access the shared folder from Ubuntu without any problem, BUT if I enable the Firestarter, it won't let me access it.
What should I do to configure Firestarter to allow my Macbook to my Ubuntu's shared folder.  Please advice.

---

### Post by wieman01 on 2007-12-28
What port does MAC usually use to access other computer? And what protocol are we talking about?

---

### Post by Dimension7 on 2007-12-30
> **wieman01 said:**
> What port does MAC usually use to access other computer? And what protocol are we talking about?

Sorry for my ignorance, but how do I find which port does my MAC access to other computer.

I'm using Samba to connect.

---

### Post by wieman01 on 2007-12-30
Ok, Samba requires these ports:
> 137-139 445
For inbound and outbound traffic please. I have attached a screenshot for reference.

---

