---
title: "[Syntax help]Simple Batch script (Use 'date' command to timestamp files?)"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by soeten on 2009-02-14
Hi,
I'm trying to timestamp an archive created by a simple batch script I've created, but I cant figure out the correct syntax. 

I figured I could use the 'date' command inside the 'tar' command, indivudualy the following commands work fine. Does anyone know how these can be "merged" together?

§ date +%d.%m-%y[%H:%M] 
§ tar cfpj logs.tar.bz2 /var/log/*

Help appreciated. ;)
-Thanks

---

### Post by ridetheteapot on 2009-02-14
DATE_STR=`date +%b%d`
tar cfpj logs-${DATE_STR}.tar.bz2 /var/log/*

try that

---

### Post by soeten on 2009-02-14
Yey, the ` did the trick. What is this symbol called, and is it used often in programing? (I'm pretty sure I've seen it in php.)

Anyway, thanks for saving my day. :)

---

### Post by ridetheteapot on 2009-02-15
I dunno if its the proper name, but i call them back ticks

I had posted almost the same question with the same mistake awhile ago... stupid ticks. they aren't used really outside of bash scripting as far as i know

---

