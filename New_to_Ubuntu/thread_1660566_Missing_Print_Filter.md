---
title: "Missing Print Filter"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by Desert Sailor on 2011-01-05
I applied the latest update today and managed to break my printer.  Question one, Is there a way to back up an update?

When I try to print to my default printer, The error in the print box says:  "Missing print filter for printer 'HP-Deskjet-6122'.

It appears that there is a filter file "hpcups" which is not found in "/usr/lib/cups/filter/"  I did a search for the file because it was working earlier, and found "hpcups.drv" in "/usr/share/cups/drv/hp".  I tried using sudo to move the file to the filter directory, but that didn't fix the problem.  

Any other ideas?  Or is this a known bug for which there is a work around?

---

### Post by TeoBigusGeekus on 2011-01-05
Try removing the printer and reinstalling it.

---

### Post by Desert Sailor on 2011-01-05
I tried the remove and reinstall, but that didn't work.  HOWEVER, I also tried something else which seems to have solved the problems. 

I used the Synaptic Manager to install HPLIP-CUPS and that seems to have fixed the problem.  

SOLVED.

---

### Post by dowcet on 2011-01-26
> **Desert Sailor said:**
> I used the Synaptic Manager to install HPLIP-CUPS and that seems to have fixed the problem.  

  This also did it for me, without a re-install, but I also had to figure out one more thing... that is, to right click on the printer icon and select "enable".

---

