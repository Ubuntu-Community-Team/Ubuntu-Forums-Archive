---
title: "ubuntu10.04 server ACPI install and run?"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by cllow2020 on 2010-05-19
How to setup ubuntu 10.04 server to run ACPI , where to verify its contain ?

---

### Post by -humanaut- on 2010-05-19
ACPI is enabled by default if you type dmesg after you login you can verify that it is running.

---

### Post by cllow2020 on 2010-05-19
how to modified its setting , like wake on lan, suspand time due....
 
currently installed [http://packages.ubuntu.com/lucid/acpi-support](http://packages.ubuntu.com/lucid/acpi-support)

---

### Post by -humanaut- on 2010-05-19
I don't use those features so I'm honestly not sure. Check your BIOS that should have a wake on lan option in it all the computers I own atleast have it or I've installed Lan cards with an onboard ROM that allows me to setup wake on lan directly from the card.

---

### Post by cllow2020 on 2010-05-19
motherboard P4M900T-M2 come with build-in lan ; RAID ; sound and CD, i see WOL source codes...etc under linux directories , sure this can be support wake on lan.
 
 but included src files need to make install to get .o file, ubuntu10.04 server version do not have the gcc compiler support. where should i make install ?????

---

### Post by cllow2020 on 2010-05-20
found it, installing gcc now....
> 
apt-get install build-essential


---

