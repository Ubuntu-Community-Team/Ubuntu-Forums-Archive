---
title: "how can i get firestarter to start when i go online"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by blake7 on 2009-07-15
if thats not possible can i get it to start when i turn on my comuter

cheers

---

### Post by philinux on 2009-07-15
Simply put you dont need to.

you're thinking Windows.

Firestarter is a gui for amending ubuntu's firewall which is iptables. Iptables is running all the time.

---

### Post by blake7 on 2009-07-15
ok that seems crazy but i take your word on it

cheers

---

### Post by philinux on 2009-07-15
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Another utility for modifying iptables is UFW, (uncomplicated fire wall). It's in synaptic

I use a gui to do any changes. I dont like command line stuff for iptables.

---

### Post by mcduck on 2009-07-15
Firestarter will start automatically on boot. The actual firewall script, that is, as the graphical user interface is just a tool for configuring the firewall script.

In other words, Firestarter GUI is tool for configuring the Firestarter script, which loads your firewall rules to iptables which does the actual filtering.

If I remember right "sudo /etc/init.d/firestarter status" should report if the script is running.

Still, if you really feel that you need a firewall I'd recommend UFW (or Gufw if you want a GUI) instead of Firestarter.

---

