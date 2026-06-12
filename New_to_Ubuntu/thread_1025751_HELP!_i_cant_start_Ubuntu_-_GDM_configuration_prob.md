---
title: "HELP! i cant start Ubuntu - GDM configuration problem"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by personal-data-removed on 2008-12-30
Hi.

I have Ubuntu "intrepid ibex" installed.
Today when i turned on the computer, i cant enter Ubunt, it appears this message: 

"Server Authorization directory (daemon/ServAuthDir) is set to /var/lib/gdm but this does not exist. Please correct GDM configuration and restart GDM"

I am typing this on a live cd, what do i do to get the system back ?
I tryed to reinstall the ubuntu-desktop but didnt worked.

---

### Post by personal-data-removed on 2008-12-30
Yesterday i did a virus check with clam.
It found 17 virus ?! (false positives i think), i think one of them was GDM (not sure), perhaps it moved GDM to quarantine.

What can i do ?
I am booting from live cd, cant access clam to restore the file.

---

### Post by personal-data-removed on 2008-12-30
SOLVED, with:

sudo apt-get purge GDM
sudo apt-get install GDM

---

### Post by personal-data-removed on 2008-12-30
Confirmed, the cause of the error was the clamtk check.

False positives.
GDM files recognized as virus.

?!

---

### Post by BatsotO on 2008-12-30
Why in the world you need antivirus anyway?

---

