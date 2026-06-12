---
title: "Xming to Ubuntu 7.04"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by BobinAlaska on 2007-05-25
I am trying to connect to my Ubunto 7.04 machine from Windows 2000. I am using Xming 6.9.0.18 and putty .6. When i try to connect I get the message, "Network error:Connection refused." When I try to connect with SSH Secure Shell 3.2.9 I am told the host is unreachable. I can ping the Ubbuntu machine and get no errors so I know the two machines can see each other. Is there something I need to do on the Ubuntu machine?

 I am new to Linux and would appreciate any pointers you may have.

Thankshttp  :)

---

### Post by spin2cool on 2007-05-25
Ubuntu desktop version doesn't ship with ssh enabled.  Install it with:

sudo apt-get install ssh

---

### Post by BobinAlaska on 2007-05-25
Thank you! Installed SSH and everything seems to be working now. :popcorn:

---

