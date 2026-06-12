---
title: "Power on log program"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by ElectRepair on 2010-02-16
I'm trying to find a program which will log each time & date the Ubuntu was powered up (booted). I would like to use it to monitor the repaired motherboard of a desktop system without actually being with it.
 
I had found a Windows program some time ago that performed this task on a Windows OS, however I've not been able to locate a similar Ubuntu program.
 
Please let me know if this type of program exists and where I could obtain it.
 
Thank You

---

### Post by Miljet on 2010-02-16
You don't need a special program to do that. Just write a one line bash script that appends the date and time to a file and include that script in your startup programs. Here is a beginners guide to bash.

[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html)

---

### Post by InspiredIndividual on 2010-02-16
I was going to say the same as Miljet, but it seems it can be done even easier. You can find out the system reboot history with ```
last reboot
```if I'm not mistaken.

---

### Post by Miljet on 2010-02-16
Nice one! And we learn something new every day.

---

### Post by ElectRepair on 2010-02-17
Thank You Both! I can sleep now instead of watching the screen saver!

---

