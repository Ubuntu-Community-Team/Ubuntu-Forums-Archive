---
title: "Yet another ... 3c574 issue"
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by Miteto on 2007-08-24
Hello everybody,
Being a Gentoo user it never crossed my mind to try any other distro. A week ago I decided to give Ubuntu family a try. I took out of the dark an old Siemens notebook and put in the tray a fresh Xubuntu Feisty CD. Besides a troublesome start everything went well. Unfortunately the eth interface of 16-bit 3Com Megahertz was not detected. I followed **[Peter Stuge's hint]("http://lists.infradead.org/pipermail/linux-pcmcia/2007-February/004391.html")** and voila - eth0 appeared. The strangest thing is that the card gets DHCP lease every other startup. I'm sure the card is ok because using a Warty LiveCD lease is recieved every time. Any ideas?
Thanks

---

### Post by Miteto on 2007-08-27
Well ... the solution was rather simple: passing two boot options - "acpi=off" & "pnpbios=off" made my day, passing either of them alone didn't help.
Next challenge - ESS1869, yeah baby !
Have a nice day people!

---

