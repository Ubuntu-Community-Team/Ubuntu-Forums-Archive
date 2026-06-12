---
title: "runaway http -  how to research this?"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by capybara on 2008-05-05
im running kubuntu 7.10 gutsy gibbon.
when im NOT doing anything on local network or internet,
i can see the activity light on my ethernet card
flashing, indicating activity. 
[same with my wifi card b4 i removed it.]
so i check out running processes, and 
pid 5519, which is called http in the KDE process table, is running.
so i enter:
sudo kill 5519
and the activity stops.
whats going on here? virus/malware?
program bug?
how do i research this?

---

### Post by Ayuthia on 2008-05-05
> **capybara said:**
> im running kubuntu 7.10 gutsy gibbon.
when im NOT doing anything on local network or internet,
i can see the activity light on my ethernet card
flashing, indicating activity. 
[same with my wifi card b4 i removed it.]
so i check out running processes, and 
pid 5519, which is called http in the KDE process table, is running.
so i enter:
sudo kill 5519
and the activity stops.
whats going on here? virus/malware?
program bug?
how do i research this?
You might try installing wireshark and see what kind of traffic is flowing through.  It will list the ip address that is it sending/receiving information and you can then figure out what is happening.

---

### Post by capybara on 2008-05-06
thx Ayuthia, wireshark was Xactly what i needed! :)

---

