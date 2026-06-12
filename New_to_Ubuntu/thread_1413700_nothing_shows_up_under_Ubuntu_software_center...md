---
title: "nothing shows up under Ubuntu software center.."
date: 2010-02-22
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-02-22
On a recent Ubuntu install.....


I go to software center, and nothing is showing up for me to get. There are also 0 items in teh installed software pane as well.

---

### Post by chaanakya_chiraag on 2010-02-22
Try running ```
sudo aptitude update
``` in a terminal (Applications->Accessories->Terminal) and see if that helps.

---

### Post by TurnOfTide on 2010-02-22
problem:

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: Couldn't rebuild package cache
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

---

### Post by Merk42 on 2010-02-22
copy/paste the contents of the file
/etc/apt/sources.list

---

### Post by TurnOfTide on 2010-02-22
I hate to be such the noob I am but I found the solution here:
[http://www.linuxquestions.org/questions/debian-26/aptdpkg-errors-varlibdpkgstatus-155478/](http://www.linuxquestions.org/questions/debian-26/aptdpkg-errors-varlibdpkgstatus-155478/)

---

### Post by chaanakya_chiraag on 2010-02-23
Please mark this thread as solved (Thread Tools -> Mark as Solved) if your problem has been resolved.  Thanks!

---

