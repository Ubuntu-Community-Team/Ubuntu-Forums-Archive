---
title: "HP Compaq 8510p and HP Compaq nc4000 wireless conection"
date: 2013-12-13
forum: Networking &amp; Wireless
---

### Post by niang on 2013-12-13
Hello everybody. I am new on this forum and seeking for help.
I have 2 laptops ( HP Compaq 8510p and HP Compaq nc4000) that I have migrated from Windows 7 to Ubuntu 10.04.
The wireless is not detected under Ubuntu. I have check in the forum and did not see any solution. Under Windows everything is ok.
Please help me.
Best regards

---

### Post by mörgæs on 2013-12-13
Hi, welcome to the fora.

10.04 is obsolete. You should begin with a fresh install (using wired internet access) of 13.10; the 8510 can run everything but the 4000 would prefer Lubuntu.

Post again if you encounter PAE problems on the 4000.

---

### Post by niang on 2013-12-20
Helo,
I have done this wht you advice. But still no WiFi connection

---

### Post by mörgæs on 2013-12-20
Please run

```
sudo lshw - sanitize > lshw.txt
```

and post lshw.txt in CODE tags.

---

