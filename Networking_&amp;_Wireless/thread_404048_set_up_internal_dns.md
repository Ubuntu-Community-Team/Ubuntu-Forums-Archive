---
title: "set up internal dns"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by insert_name_here on 2007-04-07
Can I set up a DNS server inside my LAN so that when people (obviously on the lan) want to refer to one computer, they can just use 'achilles' rather than 192.168.1.151?

Thank you

---

### Post by PurplePenguin on 2007-04-07
System -> Administration -> Networking (in Edgy)

When the Network Settings window opens, just click Hosts.  This lets you put in the ip address and whichever alias you'd like to give it.

---

### Post by insert_name_here on 2007-04-07
That would only work on the specific machine where I had made the alias, correct?

To be more specific, my situation is:  I have a server and wireless lan set up in my dorm.  The lan is not connected to the internet.  I want other people, running Windows (or linux) to be able to connect to this server to download content, either via a samba share, http or ftp.  I have samba, http and ftp set up, as well as the lan.  All I want now is that any person, in range of my router, to be able connect to the router, type 'achilles' into the address bar of firefox in the same way they now can type '192.168.1.151'.

---

### Post by wuzzerd on 2007-04-07
Check out avahi.  It should be already installed in your Ubuntu.

---

### Post by insert_name_here on 2007-04-07
Hmm... maybe what I need just isn't available, or I'm being too demandding... heh.. anyways.

Avahi doesn't work with windows - the majority of the people whom I wish to reach are n00bs - they know linux as an OS which a few nerds they know use, and it has pretty stuff (beryl).

The simpler the better, really.

---

