---
title: "Easy Firewall"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by wbee on 2009-03-28
Hello,

When I typed "firewall" into the synaptic manager,it gave me several choices.

Which one should I activate to have default allowing in nothing,unless I set a port exception for the transmission torrent software?

-----------

Thank you.

---

### Post by linuxuser21 on 2009-03-28
I'd use Firestarter.

---

### Post by Chemical Imbalance on 2009-03-28
sudo apt-get install gufw

then look in System, Administration, Firewall Configuration

Gufw is simpler than Firestarter

---

### Post by bobbob1016 on 2009-03-28
Just so you know, with a router, a software firewall is basically redundant.  It gets in the way, and takes up CPU time.  However, if you are worried about people behind the router hacking you, then a software firewall is understandable.

---

### Post by wbee on 2009-03-28
Thank you all.

---

### Post by hyper_ch on 2009-03-29
(1) You have already a firewall called iptables

(2) Firestarter, UFW etc. are nothing but configuration tools for iptables

(3) Firestarter is outdated and the ubuntu devs recommend rather ufw

(4) in most cases you don't even need to bother about firewalls and stuff. The default configuration is good (which is to let everything pass)

---

