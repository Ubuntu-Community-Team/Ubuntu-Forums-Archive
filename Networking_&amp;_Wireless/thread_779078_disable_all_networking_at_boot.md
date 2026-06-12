---
title: "disable all networking at boot"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by ufnoise on 2008-05-02
How do you disable all networking at boot?  I'd prefer not to see my wired and wireless interfaces up at boot.  I only want to see "lo".

It is greatly troubling to me that the moment I login, I see that I am already connected to the wireless connection.  I would prefer that I choose the moment to connect to the internet.

Thanks,

Juan

---

### Post by ibutho on 2008-05-02
If you run the network configuration tool there should be an option to disable interfaces being started at boot time. If you use NetworkManager, you may need to disable it and start services manually.

---

### Post by ufnoise on 2008-05-02
System->Administration->Network

Does not appear to provide any such feature.  If I try to turn off roaming for my wired connection, I can't click "Ok".

I apologize for being new to this Ubuntu thing.  But if there is a text file in some directory that will allow me to disable bringing up the interfaces at boot, I'd appreciate it.  The documentation I googled online has been unclear.

---

