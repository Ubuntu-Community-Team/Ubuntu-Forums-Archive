---
title: "DB Home-Server"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by Powl on 2008-07-28
Hello everybody,

yesterday I installed my first Linux system = ubuntu (8.04) on my Laptop and I got infected by the Ubuntu-fever. So I set up myself a

task:
- a database accessible over a home-network by a graphical interface.

hardware:

- Pentium III 700 MHz RAM 768 MB Ram
- Laptop Intel Dual-Core 1.8 GHz 1 MB Ram
- Switch

plan:
- installing Ubuntu Server on the Pentium-Machine,
- setting up a LAMP on the Ubuntu Server
- connecting the Server and the Laptop to the Switch
- using HTML, PHP and MySQL to program the DataBase and the GraphicalUserInterface

questions:
- does the plan make sense to fulfill the given task
- I have at home no Internet-Access. I can install the Ubuntu server, by downloading the iso-file and burning a CD. But how can I install the LAMP on the Ubuntu server without Internet-Access? Does it means, that I have to download the necessary packages for the LAMP installation on my Laptop and that I have to adapt the $ apt-get install "PackageName" to search for the packages on my Laptop instead of on the Internet? If this is correct, how do I that?

Thank you very much for helping,

sincerely

Powl

---

### Post by Iowan on 2008-07-28
Fortunately, the server-version of the CD has an "Install LAMP server option". I did this on a testbed machine at work, but haven't gotten to the database (or GUI) set up yet.  I'll be curious to see if there's a way to get updates (and other packages) downloaded to a separate machine (my laptop is XP) to be used as a repository.

---

### Post by Powl on 2008-07-29
Hello Iowan,

thank you for the good news. So I burn the .iso from the Server-Installation file at home and try to install the LAMP on my Pentium III. Then I will start on my application and if I need more packages, I find a way to get them.

Thank you,

Powl

---

