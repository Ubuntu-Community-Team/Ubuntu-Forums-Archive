---
title: "hopefully straight forward file location question"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by LTFC2020 on 2009-04-06
Hi 
I want to change the number of speed dials to my opera browser and am following instructions to change the .ini file
the location of which is /home/richard/.opera/opera6.ini
so far so good but the problem I have is that when I open the location /home/richard/ I see no folder for .opera - so my question is where is it?
is the location incorrect or is the file hidden?
thanks in advance

---

### Post by _Purple_ on 2009-04-06
All the filenames starting with dot are hidden files. Type in terminal:
```
ls /home/richard/.opera
```

---

### Post by LTFC2020 on 2009-04-06
ok thanks but I actually used ctrl-H in the end which I found in the drop down menu (doh! should have looked more closely to start with)
however:
new problem I added the required lines to the file i.e.

[Size]
Rows=5
Columns=5

and nothing happened!
any ideas

---

### Post by juancarlospaco on 2009-04-06
**CTRL + H**

On the Home Folder

---

### Post by _Purple_ on 2009-04-06
> **LTFC2020 said:**
> ok thanks but I actually used ctrl-H in the end which I found in the drop down menu (doh! should have looked more closely to start with)
however:
new problem I added the required lines to the file i.e.

[Size]
Rows=5
Columns=5

and nothing happened!
any ideas

Adding these lines seems to work with Opera 9.5. I am using Opera 9.65 and it doesn't work for me either.

---

### Post by _Purple_ on 2009-04-06
> **LTFC2020 said:**
> ok thanks but I actually used ctrl-H in the end which I found in the drop down menu (doh! should have looked more closely to start with)
however:
new problem I added the required lines to the file i.e.

[Size]
Rows=5
Columns=5

and nothing happened!
any ideas

Finally managed to increase the numbers of speed dials in Opera 9.65. Instead of adding those lines to the file/home/richard/.opera/opera6.ini, add them to the file /home/richard/.opera/speeddial.ini.

---

### Post by LTFC2020 on 2009-04-06
thanks purple
I went to the speeddial.ini and had a fiddly around with adding extra speed dial numbers manually but didn`t think about adding the same command as in the opera.ini
worked a treat!

---

