---
title: "making .exe file executable in 10.10"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by jotto! on 2010-11-19
I have just installed 10.10 as a clean install. I had backed up some .exe files for wine and now when I try to change permissions by clicking the make executable box, the tick disappears almost straight away. I am shown as the owner of the file so am a little unsure as to what to do next.

---

### Post by rmockler on 2010-11-19
For starters, go to the command line, key in:  gksu nautilus
Enter your password when prompted
Navigate to the folder where the .exe files are stored
Right click on the file, click properties, permission tab
Try your change

---

### Post by jotto! on 2010-11-19
Thanks for the prompt reply.... I just tried something different, copied and pasted exe file from 2nd hard drive to downloads folder and was then able to change the permissions.

Will make a note of youe code as Im sure it will come in handy!

Thanks once again!

---

### Post by exterran on 2010-11-19
> **jotto! said:**
> Thanks for the prompt reply.... I just tried something different, copied and pasted exe file from 2nd hard drive to downloads folder and was then able to change the permissions.

Will make a note of youe code as Im sure it will come in handy!

Thanks once again!

Your 2nd hard drive must be formatted FAT32, explaining why it does not accept file permissions.

---

### Post by jotto! on 2010-11-19
> **exterran said:**
> Your 2nd hard drive must be formatted FAT32, explaining why it does not accept file permissions.


You are quite correct! Dont know why I hadnt thought of that! lol.

---

