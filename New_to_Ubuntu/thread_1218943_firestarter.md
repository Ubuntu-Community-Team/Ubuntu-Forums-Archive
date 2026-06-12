---
title: "firestarter"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by kree8or on 2009-07-21
Hi,
How can i get the firestarter firewall to automatically start on system start up?

---

### Post by wojox on 2009-07-21
Go to System > Prefrences > Start Up Applications.

---

### Post by Dan_Dranath999 on 2009-07-21
mmh i don't remember the way in gnome...

In Xubuntu: Configuration/autostarted apps  
  -add new

(the names may vary, i'm translating it from my spanish installation)

I assume there should be a similar way in UBUNTU.
Anyway, i prefer **Gufw** over Firestarter

---

### Post by kpkeerthi on 2009-07-21
Firestarter is dated and is no longer maintained. Use ufw/gufw.

btw. Firestarter is just a GUI to iptables/netfilter. You don't need to have firestarter running for iptables to be active.

---

### Post by 3rdalbum on 2009-07-21
> **kpkeerthi said:**
> Firestarter is dated and is no longer maintained. Use ufw/gufw.

btw. Firestarter is just a GUI to iptables/netfilter. You don't need to have firestarter running for iptables to be active.

Agreed wholeheartedly on both counts. Firestarter is just a program that configures the inbuilt Linux firewall. UFW does the same thing. If you set your settings in Firestarter or UFW, they will work even if you remove Firestarter.

I also don't think that Firestarter is appropriate for home use. It will work, but it's overkill, and the verbose logging has a tendency to worry people ("Oh my god, my Firestarter logs say that someone's trying to hack into my computer, what do I do?"). Use UFW or its GUI frontend, gUFW.

---

