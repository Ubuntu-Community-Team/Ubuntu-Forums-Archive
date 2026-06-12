---
title: "School network with Linux Server and Linux and Windows clients"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by TeacherP on 2007-06-08
Hi All.
I need to setup a network with windows XP, 2K, 98, linux(xubuntu) clients on a CentOS or Ubuntu server.
This is for a School.  Currently I have 600 users using 70 win98 clients, 20 Win2000 clients and about 10 WinXP clients.  The file and print server runs CentOS4.4 and Samba (PDC).  Login scripts are run based on student or staff user groups, and all users are remote.  This works well for me, however, for several reasons I need to get away from windows (90% of clients) but want to be able to provide service to the staff and students with WinXP laptops.  Also i do not have server power for 90 thin clients (simultaneously).

So this is what I am looking at.
CentOS server (might switch to Ubuntu, but not right now)
Samba for windows clients (PII 350-1000MHz, 128MBRam, 3.2 - 6.4GB HDD)
??????? or Samba  for Xubuntu clients (PII 350-1000MHz, 128MBRam, 3.2 - 6.4GB HDD) to use the same /home/userX directory for windows or Linux clients

How do I startup xubuntu with no local user (besides the admin) and logon to the server with samba authentication?

What login scripts can I run to mount the shares based on group, like i do with windows clients.

Any suggestions on cloning xubuntu HDD.  I need to be able configure my client HDD and clone x 70.

Thanks in advance

---

