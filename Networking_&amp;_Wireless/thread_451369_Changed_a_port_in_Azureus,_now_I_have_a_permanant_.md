---
title: "Changed a port in Azureus, now I have a permanant NAT problem"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by jtreach on 2007-05-22
Put simply:

1. Changed the default port in Azureus to try and battle throttling
2. Forgot my old (working) port number (it was a non-standard one)
3. New port number creates NAT problem
4. Firewall is definitely configured to forward that port
5. Google / Azureus problem reveals that I need to forward / allow that port in Ubuntu itself as all ports are blocked by default? (or something along those lines, I'm not exactly an expert at these things)

Any ideas?

I saw the section on the azureus wiki aimed at this but it didn't seem to work......

[azureus wiki entry on port forwarding on ubuntu]("http://www.azureuswiki.com/index.php/NAT_problem#Port_Forwarding_on_Linux.2C_specifically_Ubuntu")

---

### Post by just learning on 2007-05-22
did you use a higher number port,like a five digit number b/c i read that the lower numbers can cause conflicts. i did that and azureus works fine. i don't know a whole lot about it either, but maybe that will work.

---

### Post by jtreach on 2007-05-22
according to some of the people on the #azureus-support channel I should make sure I have a static local ip address, but I have no idea how to do that on ubuntu, plus why would it work before but not now? surely the problem is port specific and nothing to do with my ip, as far as I know changing the port a program runs has nothing to do with ip addresses. I'm using port 52000

---

### Post by jtreach on 2007-05-22
After reboot everything seems to be fine.... azureus still seems to be slow but then again it is an 1:8 seeder:peer ratio.

---

### Post by whitetrash on 2007-05-23
if you have a router you need to forward the port in the router to your pc's ip (which is prob. why the suggested a static ip).

---

