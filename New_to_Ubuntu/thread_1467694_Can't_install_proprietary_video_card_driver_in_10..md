---
title: "Can't install proprietary video card driver in 10.04"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by theubersmurf on 2010-05-01
When I try to install the current proprietary GPU driver from my vendor, It says No such file or directory...Not sure what's happening there. Need some help with this. I tried sudo, and checked my spelling, I don't think they're the problem.

---

### Post by Chromagnum on 2010-05-01
> **theubersmurf said:**
> When I try to install the current proprietary GPU driver from my vendor, It says No such file or directory...Not sure what's happening there. Need some help with this. I tried sudo, and checked my spelling, I don't think they're the problem.

I'm just shooting blind here... last night I kinda have similar problem while using Ubuntu Software Center on my friend's laptop. There were no install option available. If there is one, when I clicked install there were some errors. 

So, I tried to change download server in Software Sources and voila, everything works. Perhaps you should try to change download server as well, see how it works for you.

---

### Post by theubersmurf on 2010-05-01
This was downloaded directly from the vendor's site.

---

### Post by swoll1980 on 2010-05-01
What kind of card do you have?

---

### Post by theubersmurf on 2010-05-01
Radeon 5850

---

### Post by Chromagnum on 2010-05-01
> **theubersmurf said:**
> This was downloaded directly from the vendor's site.

Oh, I'm sorry. I thought... oh well, nevermind. Then, I don't know man. But on related note, why you didn't use proprietary driver from Ubuntu — the jockey one?

---

### Post by swoll1980 on 2010-05-01
I should have read the op better. Your having a path issue. You either misspelled something or missed a . - or what ever. It's case sensitive too so use UPPERCASE and lowercase appropriately. make sure slash are in the right places. What is the name of the file, and what folder is it in. Downloads should be in ~/Downloads/ with a capital D then the name of the file.

---

### Post by theubersmurf on 2010-05-01
THe driver available via the driver install utility is working well, so I'm using that for the moment. As long as it's functioning reasonably well it's ok. In Koala, the drivers were usually out of date, and didn't support this (relatively new) card...something's different somehow]

---

### Post by 3rdalbum on 2010-05-01
A binary installer needs to have 'execute' permission - see the 'chmod' command.

Also you can drag the file to the terminal to put its path into the terminal, no need to type it.

---

### Post by Jive Turkey on 2010-05-01
If it was a downloaded installer file *.run or something like that, you may have to make it executable using the command:```
chmod +x ~/Downloads/<file name>
``` assuming you downloaded it to there.

The error you mentioned will come up if its not executable yet.  Also know it must be run with root privileges, and it would work best if you run it from a command shell after stopping GDM/X11.  If the driver offered in the repos works ok I would stick with that one though.

---

