---
title: "i can't access some folders in home"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by M.Salah on 2009-11-26
Hi all[INDENT] i install ubuntu since one week ago to install oracle E business suite on it , so i am very new to ubuntu , i have the application under

 [php]/home/msalah/oracle E business suite/[/php]i try to access this folder but there are error message like this:
[php]bash: cd:/home/msalah/oracle E business suite/ No such file or directory[/php]
and if i try to access the 
[php]/home/msalah/[/php]
it give me the same error
i will spend more time in learn ubuntu but now i want to install the application
[/INDENT]Regards
M.salah

---

### Post by mbzn on 2009-11-26
hi there

I believe msalah is your username and the user that is currently loged in

Try:
cd ~/oracle\ E\ business\ suite/

---

### Post by M.Salah on 2009-11-26
> **mbzn said:**
> hi there

I believe msalah is your username and the user that is currently loged in

Try:
cd ~/oracle\ E\ business\ suite/

Thanks it work, but if i have it in a ntfs drive how i can access it
Regards

---

### Post by NFblaze on 2009-11-26
Yes. M.Salah, it looked like your problem was the spaces.

For future reference if you have spaces in your file path you must either backslash (also called escape) them out, by placing the '**[COLOR="Red"]\[/COLOR]**' symbol **before the space**. Like mzbn showed:

[I]home/masalah/oracle[COLOR="Red"]**\**[/COLOR] E[COLOR="Red"]**\**[/COLOR] business[COLOR="Red"]**\**[/COLOR] suite/
[/I]

Or put the whole title in double quotes **[COLOR="Red"]" "[/COLOR]** like:

*[COLOR="Red"]**"**[/COLOR]/home/msalah/oracle E business suite/[COLOR="Red"]**"**[/COLOR]*

Also, you can use the **TAB** button when typing in a path to attempt to auto type the correct path for you.

---

### Post by mbzn on 2009-11-26
First you need to mount the ntfs partition, Here's how
[http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/](http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/)

browse to the mounted folder ie cd /media/c
then the directory it is in. 
What type of file is it that you would like to install?

---

