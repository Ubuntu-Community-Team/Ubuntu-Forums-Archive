---
title: "Cannot connect to the internet"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by timmy-g on 2007-11-13
Hello,
I'm using a Sony Vaio PCGR600 on **XUBUNTU ** and have a Belkin Wireless G router.
My laptop "sees" my wifi but for some reason i cannot actually connect!
Any help would be much appreciated ;)

:confused:

---

### Post by ddrichardson on 2007-11-13
There is a troubleshooting guide in the system help for Ubuntu but I don't know if it made it into Xubuntu, however most times you can see but not connect the problem is the driver. What wifi card does this machine have?

---

### Post by timmy-g on 2007-11-13
does this help
Modem =built-in modem V.90/K56Flex (56kbps) data/fax modem

Sorry...

---

### Post by ddrichardson on 2007-11-13
No, that's a modem not a wireless card, open a terminal and type```
sudo lshw -class network
```That should tell you what wireless card you have.

---

