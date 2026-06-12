---
title: "Security for Dummies?"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by monocongo on 2007-03-04
I would like to add basic security to my home desktop system.  I assume that Linux is more secure than Windows by default, but I also assume that there are some simple things you can do which will give you a bit more security than what you get out of the box (such as basic firewall and antivirus programs).  I don't have the time or inclination to get into writing scripts for iptables, etc., and I don't expect to be able to keep serious crackers out, but if there are some simple things which I can do in order to lock down my system a wee bit then I'd like to put these in place.

Mine is a stand-alone home desktop system which is used primarily for surfing the web.  I am connected to a wireless router (Motorola WR850G) which is connected to a cable modem.

Thanks in advance for any suggestions, comments, etc.

---

### Post by ffxr on 2007-03-04
well.. lock down your router with WPA encyrytion, & MAC control

u could install firestarter as firewall, there really is no need for anti virus.. & 'serious crackers' will not be interested in the average desktop pc..anyway

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by gradedcheese on 2007-03-04
By default, ubuntu doesn't really ship with a lot of ports open.  There's not much that a malicious user can do to break in, at least not until you install more stuff that opens ports and provides services to attack.  This commonly would be a web server and so on.  I wouldn't bother with firestarter or the like unless you have more specific needs.

---

