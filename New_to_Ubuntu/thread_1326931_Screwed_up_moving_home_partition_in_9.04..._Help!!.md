---
title: "Screwed up moving home partition in 9.04... Help!!"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by kendoori on 2009-11-14
I followed the psychocats guide to moving home to another partition, but ran into the dreaded ICEauthority file issue, and regardless of the remedies I used to try to correct the permissions problems, couldn't get it to work. I decided to revert, but alas that didn't work either.

Whatever commands I used to revert the backed up home directory, now have placed my original home files in /home/home_backup/kendoori

Everything is intact in this tree...

I'm pretty green about shell commands, so would appreciate if someone could just give me the magic that will move everything from  /home/home_backup/kendoori so that it resides properly under /home/kendoori

I'm a bit shell shocked after the failed previous move, especially since I believe that somehow the permissions didn't make it over properly.

---

### Post by mt1234 on 2009-11-14
I'm new to Linux, so maybe there's something I'm missing, but can't you just use Nautilus to create a new folder under Home named kendoori, then move all of the contents of  /home/home_backup/kendoori to /home/kendoori?

---

### Post by kendoori on 2009-11-15
thei issue is that I can't login, so can't use Nautilus. I will try using Live CD and see what shakes.

---

