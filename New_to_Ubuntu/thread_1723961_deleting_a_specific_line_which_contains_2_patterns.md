---
title: "deleting a specific line which contains 2 patterns"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by quartaela on 2011-04-07
hi there i have a problem about deleting a line from a text file which contains two specific patterns. i am using
"sed -i "/$name\ d" peop.txt" but i must use one more variable which is surname. so how can i do that_?. and thx for your help : ) 

"
burak:ak:3242:2342:dsa@a.com
gokhan:okan:432:4234:da@a.com
"

and this is the code of text file.

---

### Post by rampageoberon on 2011-04-07
Try and see if the below code works

```
sed -i '/$string/ d' <file>
```

---

### Post by quartaela on 2011-04-07
> **rampageoberon said:**
> Try and see if the below code works

```
sed -i '/$string/ d' <file>
```
well that code isn't working the solution is "sed -i "/$name/ d" file.txt" but this is working for only one pattern. want to check the name and the surname. the database looks like

"Ava:Gardner:24-12-1982:+23232774009:gava@peop232.com
James:Dean:08-02-1991:+2323246729:jdean@peop232.com
Audrey:Hepburn:04-05-1989:+2322064386:tiffany@peop232.com
Frank:Sinatra:12-12-1975:+2326039314:bluemoon@peop232.com"

and i am trying to makin this operation

"DELETE A CONTACT
----------------------------------
Please enter name: Ava
Please enter surname: Gardner
Contact is deleted from the database"

but as i said "sed -i "/$name/ d" file.txt" works for only name : )

---

