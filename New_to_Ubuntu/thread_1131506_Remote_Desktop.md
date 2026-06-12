---
title: "Remote Desktop"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by Frank_F on 2009-04-20
Hello,

Just configured remote desktop on my ubuntu server to allow other users to view you desktop.

Trying to connect my laptop (also Ubuntu), using command vncviewer ip:0 but received error thst command is not found

---

### Post by juancarlospaco on 2009-04-20
*vnc server is runing on ubuntu server ?*

---

### Post by Frank_F on 2009-04-20
Yes it is working...i can actually vinagre frank-desktop:o on the machine to itself but not on my latop...I changed the port to 80 to remove any possiblity of router or firewall issue since I a running apache server with no issues

Thanks

---

### Post by HermanAB on 2009-04-20
You can debug connectivity issues with telnet:
$ telnet 1.2.3.4 80

and you should get a banner.  If not, then a router or firewall is preventing access, so move you test point and try again to narrow it down.

---

### Post by Frank_F on 2009-04-20
Hi, i am able to ssh frank@1.2.4.1 and login via command line.

---

### Post by jdmorris on 2009-04-20
Sometimes you need to have administrator right to view other desktop.

---

### Post by Frank_F on 2009-04-21
I have just checked firewall and router and they are open at port 5900, which what I now set my remote desktop too.

How do i get admin rights, i am using sudo vinagre xxxx-desktop:0 .....any other ideas ?

---

