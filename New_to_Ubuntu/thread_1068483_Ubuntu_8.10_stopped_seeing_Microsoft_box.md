---
title: "Ubuntu 8.10 stopped seeing Microsoft box"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by Jim Rimedio on 2009-02-12
I have a box running Microsoft Windows XP Professional Version 2002 with Service Pack 3.  That box has an Intel(R) Celeron(R)CPU2.66GHz, 2.67GHz 1.00 GB of Ram.  I have a Linux box running Ubuntu 8.10.

	In the past I was able to access the Microsoft box on Ubuntu 8.10 via Places, Network, Windows Network, Workgroup, BlackComputer (the Microsoft's computer name).  Thereafter,  “BlackComputer” appeared in Places.  I was able to access all files in the Microsoft box via the Ubuntu 8.10 box and could print anything from the Ubuntu 8.10 box on the printer attached to the Microsoft box.

	Today, when I followed the procedure, in the Location box the following is present “smb://blackcomputer/”, but nothing appears below the word “Name”.  Ubuntu 8.10 is not seeing the Microsoft Box.

	Is there a way to mount the BlackComputer using the Terminal?  Is there a way to automatically mount or otherwise cause the network connection each time I boot?  Is there a way to return to the original way of accessing the BlackComputer.

	Programs that normally would print from the Ubuntu 8.10 to the Microsoft box printer do not print.  In fact after giving the print command, when I check System, Administration, Printing, the print queue is empty.

	What is the fix?

---

### Post by Peter09 on 2009-02-13
This sounds like a permissions problem, have you done anything on either box lately?

---

### Post by Jim Rimedio on 2009-02-21
To the best of my knowledge I have not made any changes in the Ubuntu 8.10 box.  Is there a was to connect using the terminal?

---

### Post by superprash2003 on 2009-02-21
try using smb://x.x.x.x where x.x.x.x is the ip.. instead of hostname

---

