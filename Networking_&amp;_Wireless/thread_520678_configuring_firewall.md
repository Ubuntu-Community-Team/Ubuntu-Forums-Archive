---
title: "configuring firewall"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by jacob01 on 2007-08-08
i installed firesterter firewall from the repository and checked it using the recommended firewall tester but it keeps failing because it is receiving my ping 

and when i log out and log back in i have to start the firewall back up so i was wondering if i could set it to have it start up when i log in instead of starting it every time i log in

---

### Post by ruibernardo on 2007-08-09
Hi jacob01,

> **jacob01 said:**
> i installed firesterter firewall ... but it keeps failing because it is receiving my ping 

What do you mean when you say "because it is receiving my ping".

> **jacob01 said:**
>  and when i log out and log back in i have to start the firewall back up 

You don't have to start Firestarter when you log in. Firestarter is a graphical user interface to use iptables (the real firewall). Firestarter and iptables are always working on the background, even if you don't have the GUI on your desktop. You only have to run it once to configure it and enable it (running it the first time should start the "Assistant" to do this).

But if you do want to see Firestarter when you login, take look at this page: [http://www.howtoadvice.com/AutoFirestarter/](http://www.howtoadvice.com/AutoFirestarter/)

Hope this helps. :)

---

### Post by ruibernardo on 2007-08-09
> **jacob01 said:**
> but it keeps failing because it is receiving my ping 

Ok, I think this means that you didn't run Firestarter Wizar (I've called it "Assistent" in the previous post)

Check this page to use Firestarter the right way: [http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html)

---

