---
title: "Can I move all windows fonts?"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by rams123 on 2009-05-13
I wanna move all windows to /usr/share/fonts/truetype. Am I doing correct? Is it OK? What happens when I do that? 

Will that slow down my PC? 

Shall I've to remove msttcorefonts package?

---

### Post by achase79 on 2009-05-13
I would create a new directory within truetype to put the fonts into.  This should allow the fonts to be seen by applications within your system.  I usually go the single user route and put it in a .Fonts folder within my home folder.

---

### Post by konqueror7 on 2009-05-13
what i do is just paste it all in */home/<user>/.fonts*....\:D

---

### Post by Don1500 on 2009-05-13
> I wanna move all windows to /usr/share/fonts/truetype. Am I doing correct? Is it OK? What happens when I do that? 


Leave your fonts where they are for windows, follow the instructions below and make a second directory for Ubuntu. If you put the fonts into an ext3 partition Windows will not see them.



Here are instructions on how to install truetype fonts on Ubuntu: [http://www.arsgeek.com/2007/07/19/how-to-install-truetype-fonts-on-your-ubuntu-computer/](http://www.arsgeek.com/2007/07/19/how-to-install-truetype-fonts-on-your-ubuntu-computer/)

---

### Post by rams123 on 2009-05-13
> **konqueror7 said:**
> what i do is just paste it all in */home/<user>/.fonts*....\:D

There is no .fonts folder in home, even in hidden files.

I can only see .fontconfig folder there.
> **Don1500 said:**
> Leave your fonts where they are for windows, follow the instructions below and make a second directory for Ubuntu. If you put the fonts into an ext3 partition Windows will not see them.


I just wanna COPY and paste all win fonts to ubuntu, because I just wanna use them in Ubuntu. And some sites are looking ugly in ubuntu and good in win, so it will help here too. Correct me if I am wrong.

I am NOT doing cut/paste.

---

### Post by Don1500 on 2009-05-13
This will tell you how to get all your TTfonts that you have in Windows and activate them for Ubuntu, and they will look good. It is not just a copy and paste operation.

[http://www.arsgeek.com/2007/07/19/how-to-install-truetype-fonts-on-your-ubuntu-computer/](http://www.arsgeek.com/2007/07/19/how-to-install-truetype-fonts-on-your-ubuntu-computer/)


Sorry about the previous bad link, it's been fixed.

---

### Post by konqueror7 on 2009-05-13
just create a new folder named '.fonts', the fonts inside will just be loaded automatically...

---

