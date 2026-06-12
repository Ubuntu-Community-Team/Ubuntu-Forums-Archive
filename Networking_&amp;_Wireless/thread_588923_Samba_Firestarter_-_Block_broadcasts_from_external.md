---
title: "Samba Firestarter - Block broadcasts from external network"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by drpepper on 2007-10-23
Hey guys

I set all the rules up etc for other clients on my network to access the samba share on my Linux box. But unless I've unchecked the option in Firestarter->Preferences->Firewall->Advanced->Block broadcasts from external network on the sharing box i.e; NOT blocking broadcasts from external network the other clients can't see the share. Why is this, and is it dangerous to have this option off?

Cheers Guys

Nick

---

### Post by froy02 on 2007-10-23
Networks won't connect if firestarter is on.  From what I read from forums it is not needed for linux. Linux is not windows, it is a lot safer.   But if you want use it just stop it when you want to access other computers from your network.  


Very satisfied Ubuntu convert.
Froy,

---

### Post by drpepper on 2007-10-24
Linux comes with a firewall built in, called iptables. Firestarter is simply a GUI to edit these iptables...

---

