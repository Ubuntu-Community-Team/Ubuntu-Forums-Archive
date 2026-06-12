---
title: "Disconnection problems with dialup modem!"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by AN@S on 2007-05-13
Hello, 

I have a problem with my external dialup modem, I'm new to ubuntu and new to Linux; I've searched for tutorials about how to configure a dialup connection with an external modem, I followed some tutorial and configured an account using the pppconfig tool and I'm able to connect successfully but the problem is that I experience a lot of disconnections. Sometimes the modem disconnects after one or two minutes, sometimes after 20 or 30 minutes.

I also tried to configure an account through the kppp software, when I connect through the kppp I don't have disconnections but the connection is too slow.

Do you have some idea about these problems? I use feisty.

Thanks in advance

---

### Post by unisol on 2007-05-13
wvdial is part of the distro. Find the HowTo document for dialups. Therer are
a few additions to that document, like eliminating colons and adding
S19=0 to the init string, but it is easy. Don't worry.

---

