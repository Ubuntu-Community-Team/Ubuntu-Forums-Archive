---
title: "space inbtween date and time"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-07-31
echo "testavast`date +%m-%d-%Y%l:%M:%S%P`" | cat >> /home/lance/report/update.txt

i get 
testavast07-31-201012:29:29pm

how do i get a space between the date 2010 and the time 12:29:29pm

---

### Post by davidmohammed on 2010-07-31
I've just run your echo statement - seems to work fine...


dad@ubuntu-laptop:~$ echo "testavast`date +%m-%d-%Y%l:%M:%S%P`" 
testavast07-31-2010 7:40:56pm
dad@ubuntu-laptop:~$

---

### Post by iponeverything on 2010-07-31
```
echo "testavast`date '+%m-%d-%Y %l:%M:%S%P'`" >> /home/lance/report/update.txt
```

---

