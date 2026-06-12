---
title: "sbackup question"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by Old Jimma on 2009-01-01
Hi Ubuntu Community:

I'm going to use sbackup to backup my files.

Sbackup suggests that you back up the following paths:

/var
/home
/usr/local
/etc

Here are some questions:

[LIST=1]
[*]Do these choices imply that every file and directory beneath those paths will be backed up, also?
[*]What is the value of backing up the /var directory? What is in there?
[*]What is the value of backing up /usr/local? What is in there?
[*]What is the value of backing up /etc? What is in there?
[/LIST]

I realize these might be pretty stupid questions... and if truth be told, I have no excuse! But I'm just an old man and I really don't know!

:-D

Also, here is my last question:

I've something really goes bad, if I do a restore using the suggested choices, will a working system be restored that has all of my data (in /home I presume) and programs?

Thank you!
Phil Smith
Possibly the World's Oldest Ubuntu User
Duluth, GA

---

### Post by hyper_ch on 2009-01-01
> **Phil Smith said:**
> Do these choices imply that every file and directory beneath those paths will be backed up, also?

I'd say yes
> **Phil Smith said:**
> What is the value of backing up the /var directory? What is in there?
In the /var folder you normally have the webroot, the mysql dbs, the log files and a few other things...

> **Phil Smith said:**
> What is the value of backing up /usr/local? What is in there?
no clue

> **Phil Smith said:**
> What is the value of backing up /etc? What is in there?
Did you have a look at whats in there?

> **Phil Smith said:**
> I've something really goes bad, if I do a restore using the suggested choices, will a working system be restored that has all of my data (in /home I presume) and programs?
settings yes, programs no....

---

### Post by chrisod on 2009-01-01
All I back up from my laptop is my  home directory. /var and the others contains program data and program executables. Those can be reinstalled if your system gets hosed, and in fact most of it will come with a new Ubuntu install anyway. My email and browser data is all synched online so it's recoverable if necessary. If you have a highly customized system you may want to back up more. 

However, it's personal preference. I'm sure somebody will have a very good reason for backing up more than I do, and I may learn something in the process :)

---

### Post by Old Jimma on 2009-01-01
Thank you, again, Chrisrod!!!

Happy New Year!

Best regards,
Phil

---

