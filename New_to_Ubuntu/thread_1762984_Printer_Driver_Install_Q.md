---
title: "Printer Driver Install Q"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by Joelbruce on 2011-05-19
I downloaded the driver program for an hp printer and put it on the desktop. Per instructions from hp I opened a terminal box and typed in sh hplip-3.11.5.run and hit enter. I got the answer, Can't open hplip-3.11.5.run. I am running Ubuntu 10.04. Any ideas?

---

### Post by wolfen69 on 2011-05-19
Put the folder that contains the hplip-3.11.5.run file into home, then do
```
cd name_of_folder
```
then run
```
sudo sh hplip-3.11.5.run 
```

---

### Post by Joelbruce on 2011-05-20
Thank you Wolfen69. I have nominated you for sainthood in a rather obscure church. For other novices, when I did the sudo command, my keyboard did not actually print out my password, but it still worked when I typed it and hit enter as if it had been on the screen.

---

### Post by Joelbruce on 2011-05-20
Oops! It took the program and detects the printer, but it doesn't print. The printer is an hp deskjet 1000 j 110 series for which the hplip 3.11.5 is specified. I will look around the forum, but if anyone knows the answer all help is appreciated. The "preparing to print" window seems normal, but the "printing" windows appears for a couple of tenths of a second and then disappears.

---

