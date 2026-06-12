---
title: "Accessing Linux box on vacation from laptop and edit Oracle database"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by tahahellion on 2006-10-13
I want to know how to access the Linux box, through my laptop if I am on vacation.I need to be able to bring up Oracle on the Linux box,start apache,edit PHP files and the database tables.
I could keep the Linux box running with all the stuff running on it and go an vacation as well...still be able to access the files etc.

P.S. Linux box means the PC where Linux is installed

---

### Post by marianom on 2006-10-17
I let you know how I'm doing it right now:
1- Installed OpenVPN Server in the machine where the db resides
2- build keys.
3- Installed OpenVPN client in my machine
4- proper port forwarding.
5- Several methods to access the machine from then on: ssh to edit files with vim and save them, stop and start services. scp to transfer files from the client to the machine and viceversa.
6- an oracle client in my machine with proper tnsnames.ora configured and accesing the db with several tools (jdev, sql developer, sql plus).
7- I also access OEM directly from firefox.

All work ok and several of my colleagues uses it on daily basis.

---

