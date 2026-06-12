---
title: "[SOLVED] Share Window 98SE printer in ubuntu 8.04"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by gkaucher on 2008-11-30
I have an Epson CX7000F printer connected via USB to Windows 98SE desktop. My laptop is dual boot XP/Ubuntu 8.04. I am trying to get Ubuntu to print on the  Windows 98SE printer. Samba was able to recognize the location of the printer when I used the browse function, but the "verify" was unsuccesful, getting the message - "Inaccessible - this print share is inaccessible". Any suggestions appreciated.

Gary

---

### Post by superprash2003 on 2008-12-01
does it require some authentication ( username and password) to connect to the printer?? ensure you type in the right username and password

---

### Post by gkaucher on 2008-12-01
When I set up the printer share on the windows 98 side I didn't create a username or password, so I don't imagine one is necessary. I was able to share the 98 desktop printer with the XP side of the dual boot laptop without using a password. I'm assuming the username would not be the name of the printer.

---

### Post by superprash2003 on 2008-12-02
did you uncheck " authentication required" ?

---

### Post by gkaucher on 2008-12-02
I'm not sure what I did, but the printer works! I suspect that something that I did last night "fixed" the problem, but it wasn't until I rebooted everything today that the "fix" took effect. One thing that I did was manually change the IP address associated with my laptop computer in System, Admin, Network, Hosts. Maybe that was it?

---

### Post by superprash2003 on 2008-12-03
possible :).Please mark thread as SOLVED.

---

